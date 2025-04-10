[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/53CzHyEu)
Name-Naman Seth
UID -22BCS12224
AVERAGE LEARNER ASSIGNMENT 

Ques 1:

class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        int[] result = new int[nums1.length];
        for (int i = 0; i < nums1.length; i++) {
            int num1 = nums1[i];
            int indexInNums2 = -1;
            for (int j = 0; j < nums2.length; j++) {
                if (nums2[j] == num1) {
                    indexInNums2 = j;
                    break;
                }
            }
            int nextGreater = -1;
            for (int j = indexInNums2 + 1; j < nums2.length; j++) {
                if (nums2[j] > num1) {
                    nextGreater = nums2[j];
                    break;
                }
            }
            result[i] = nextGreater;
        }
        return result;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();

        // Test case 1
        int[] nums1_1 = {4, 1, 2};
        int[] nums2_1 = {1, 3, 4, 2};
        int[] result1 = solution.nextGreaterElement(nums1_1, nums2_1);
        System.out.print("Output 1: ");
        for (int num : result1) {
            System.out.print(num + " ");
        }
        System.out.println();

        // Test case 2
        int[] nums1_2 = {2, 4};
        int[] nums2_2 = {1, 2, 3, 4};
        int[] result2 = solution.nextGreaterElement(nums1_2, nums2_2);
        System.out.print("Output 2: ");
        for (int num : result2) {
            System.out.print(num + " ");
        }
        System.out.println();

        // test case 3
        int[] nums1_3 = {1,3,5,2,4};
        int[] nums2_3 = {6,5,4,3,2,1,7};
        int[] result3 = solution.nextGreaterElement(nums1_3, nums2_3);
        System.out.print("Output 3: ");
        for(int num : result3){
            System.out.print(num + " ");
        }
        System.out.println();
    }
}
Output:
Output 1: -1 3 -1 
Output 2: 3 -1 
Output 3: 7 7 7 7 7

Ques 2:

class Animal {
    String name;

    Animal(String name) {
        this.name = name;
    }

    void makeSound() {
        System.out.println("Animal makes a sound.");
    }

    void displayInfo() {
        System.out.println("Name: " + name);
    }
}

class Dog extends Animal {
    String breed;

    Dog(String name, String breed) {
        super(name); // Call the constructor of the base class
        this.breed = breed;
    }

    @Override // Override the makeSound() method
    void makeSound() {
        System.out.println("Dog barks: Woof!");
    }

    void displayBreed() {
        System.out.println("Breed: " + breed);
    }
}

public class InheritanceExample {
    public static void main(String[] args) {
        Animal animal = new Animal("Generic Animal");
        Dog dog = new Dog("Buddy", "Golden Retriever");

        System.out.println("--- Animal Information ---");
        animal.displayInfo();
        animal.makeSound();

        System.out.println("\n--- Dog Information ---");
        dog.displayInfo(); // Inherited from Animal
        dog.makeSound(); // Overridden method
        dog.displayBreed();
    }
}
Output:
--- Animal Information ---
Name: Generic Animal
Animal makes a sound.

--- Dog Information ---
Name: Buddy
Dog barks: Woof!
Breed: Golden Retriever

Ques 3:

public class StringEncoding {

    public static String[] encodeStrings(String str1, String str2, String str3) {
        String[] parts1 = splitString(str1);
        String[] parts2 = splitString(str2);
        String[] parts3 = splitString(str3);

        String output1 = parts1[0] + parts2[1] + parts3[2];
        String output2 = parts1[1] + parts2[2] + parts3[0];
        String output3 = parts1[2] + parts2[0] + parts3[1];

        output3 = toggleCase(output3);

        return new String[]{output1, output2, output3};
    }

    public static String[] splitString(String str) {
        int length = str.length();
        int partLength = length / 3;
        int remainder = length % 3;

        String front, middle, end;

        if (remainder == 0) {
            front = str.substring(0, partLength);
            middle = str.substring(partLength, 2 * partLength);
            end = str.substring(2 * partLength);
        } else if (remainder == 1) {
            front = str.substring(0, partLength);
            middle = str.substring(partLength, 2 * partLength + 1);
            end = str.substring(2 * partLength + 1);
        } else { // remainder == 2
            front = str.substring(0, partLength + 1);
            middle = str.substring(partLength + 1, 2 * partLength + 1);
            end = str.substring(2 * partLength + 1);
        }

        return new String[]{front, middle, end};
    }

    public static String toggleCase(String str) {
        StringBuilder result = new StringBuilder();
        for (char c : str.toCharArray()) {
            if (Character.isLowerCase(c)) {
                result.append(Character.toUpperCase(c));
            } else if (Character.isUpperCase(c)) {
                result.append(Character.toLowerCase(c));
            } else {
                result.append(c); // Keep non-alphabetic characters as they are
            }
        }
        return result.toString();
    }

    public static void main(String[] args) {
        String str1 = "John";
        String str2 = "Johny";
        String str3 = "Janardhan";

        String[] encodedStrings = encodeStrings(str1, str2, str3);

        System.out.println("Output1 = " + encodedStrings[0]);
        System.out.println("Output2 = " + encodedStrings[1]);
        System.out.println("Output3 = " + encodedStrings[2]);

        String str4 = "abc";
        String str5 = "defg";
        String str6 = "hijklmno";

        encodedStrings = encodeStrings(str4, str5, str6);

        System.out.println("\nOutput1 = " + encodedStrings[0]);
        System.out.println("Output2 = " + encodedStrings[1]);
        System.out.println("Output3 = " + encodedStrings[2]);
    }
}
Output:
Output1 = Jhhan
Output2 = ohnyJan
Output3 = NJOARD

Output1 = adefmno
Output2 = bcgijk
Output3 = HIJABC

Ques 4:

public class MathOperations {

    // Method to add two integers
    public int add(int a, int b) {
        return a + b;
    }

    // Method to add three integers
    public int add(int a, int b, int c) {
        return a + b + c;
    }

    // Method to add two doubles
    public double add(double a, double b) {
        return a + b;
    }

    // Method to multiply two integers
    public int multiply(int a, int b) {
        return a * b;
    }

    // Method to multiply three doubles.
    public double multiply (double a, double b, double c){
        return a * b * c;
    }


    public static void main(String[] args) {
        MathOperations math = new MathOperations();

        System.out.println("Adding two integers: " + math.add(5, 10));
        System.out.println("Adding three integers: " + math.add(5, 10, 15));
        System.out.println("Adding two doubles: " + math.add(3.5, 2.5));
        System.out.println("Multiplying two integers: " + math.multiply(4, 6));
        System.out.println("Multiplying three doubles: " + math.multiply(2.5, 2.0, 3.0));

    }
}
Output:
Adding two integers: 15
Adding three integers: 30
Adding two doubles: 6.0
Multiplying two integers: 24
Multiplying three doubles: 15.0

Ques 5:

public class AlphabetEncoding {

    public static String encodeString(String input) {
        if (input == null || input.isEmpty()) {
            return "";
        }

        StringBuilder result = new StringBuilder();
        for (int i = 0; i < input.length(); i++) {
            char currentChar = input.charAt(i);
            result.append(currentChar);

            if (i < input.length() - 1) {
                char nextChar = input.charAt(i + 1);

                if (Character.isLetter(currentChar) && Character.isLetter(nextChar)) {
                    int currentValue = getAlphabetValue(currentChar);
                    int nextValue = getAlphabetValue(nextChar);
                    int sum = currentValue + nextValue;
                    int remainder = sum % 26;

                    if (remainder == 0) {
                        result.append('0');
                    } else {
                        result.append((char) ('a' + remainder - 1));
                    }
                }
            }
        }
        return result.toString().toLowerCase();
    }

    private static int getAlphabetValue(char c) {
        if (Character.isLowerCase(c)) {
            return c - 'a' + 1;
        } else {
            return c - 'A' + 1;
        }
    }

    public static void main(String[] args) {
        System.out.println(encodeString("ay")); // a0y
        System.out.println(encodeString("ac")); // adc
        System.out.println(encodeString("12")); // 12
        System.out.println(encodeString("1a")); // 1a
        System.out.println(encodeString("ac 12a")); // adc 12a
        System.out.println(encodeString("ABC")); // abcdbc
        System.out.println(encodeString("xyz")); // xyzaaz
        System.out.println(encodeString("")); // ""
        System.out.println(encodeString(null)); // ""
    }
}
Output:
a0y
adc
12
1a
adc 12a
abcdbc
xyzaaz
