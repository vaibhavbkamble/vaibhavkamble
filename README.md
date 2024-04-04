# vaibhavkamble

Q1: Merge two arrays by satisfying given constraints
Given two sorted arrays X[] and Y[] of size m and n each where m >= n and X[] has exactly n vacant cells,
 merge elements of Y[] in their correct position in array X[], i.e., merge (X, Y) by keeping the sorted order.

For example,

Input: X[] = { 0, 2, 0, 3, 0, 5, 6, 0, 0 }
Y[] = { 1, 8, 9, 10, 15 } The vacant cells in X[] is represented by 0 
Output: X[] = { 1, 2, 3, 5, 6, 8, 9, 10, 15 }

import java.util.Arrays;

public class MergeArrays {
    public static void main(String[] args) {
        int[] X = {0, 2, 0, 3, 0, 5, 6, 0, 0};
        int[] Y = {1, 8, 9, 10, 15};

        mergeArrays(X, Y);
        System.out.println(Arrays.toString(X));
    }

    public static void mergeArrays(int[] X, int[] Y) {
        int i = X.length - Y.length - 1;
        int j = Y.length - 1;
        int k = X.length - 1;

        while (j >= 0) {
            if (i >= 0 && X[i] > Y[j]) {
                X[k] = X[i];
                i--;
            } else {
                X[k] = Y[j];
                j--;
            }
            k--;
        }
    }
}



Q2:Find maximum sum path involving elements of given arrays
Given two sorted arrays of integers, find a maximum sum path involving elements of both arrays whose sum is maximum. 
We can start from either array, but we can switch between arrays only through its common elements.

For example,

Input: X = { 3, 6, 7, 8, 10, 12, 15, 18, 100 }
Y = { 1, 2, 3, 5, 7, 9, 10, 11, 15, 16, 18, 25, 50 }  
The maximum sum path is: 1 —> 2 —> 3 —> 6 —> 7 —> 9 —> 10 —> 12 —> 15 —> 16 —> 18 —> 100 
The maximum sum is 199

public class MaxSumPath {
    public static void main(String[] args) {
        int[] X = {3, 6, 7, 8, 10, 12, 15, 18, 100};
        int[] Y = {1, 2, 3, 5, 7, 9, 10, 11, 15, 16, 18, 25, 50};

        int maxSum = findMaxSumPath(X, Y);
        System.out.println("The maximum sum path involving elements of both arrays is: " + maxSum);
    }

    public static int findMaxSumPath(int[] X, int[] Y) {
        int i = 0, j = 0;
        int sumX = 0, sumY = 0;
        int result = 0;

        while (i < X.length && j < Y.length) {
            if (X[i] < Y[j]) {
                sumX += X[i];
                i++;
            } else if (X[i] > Y[j]) {
                sumY += Y[j];
                j++;
            } else {
                result += Math.max(sumX, sumY) + X[i];
                sumX = 0;
                sumY = 0;
                i++;
                j++;
            }
        }

        while (i < X.length) {
            sumX += X[i];
            i++;
        }
        while (j < Y.length) {
            sumY += Y[j];
            j++;
        }

        result += Math.max(sumX, sumY);
        return result;
    }
}

Q3:Write a Java Program to count the number of words in a string using HashMap.

import java.util.HashMap;
import java.util.Map;

public class WordCount {
    public static void main(String[] args) {
        String inputString = "Write a Java Program to count the number of words in a string using HashMap";
        int wordCount = countWords(inputString);
        System.out.println("Number of words in the string: " + wordCount);
    }

    public static int countWords(String s) {
        String[] words = s.split("\\s+");
        Map<String, Integer> wordFrequency = new HashMap<>();

        for (String word : words) {
            wordFrequency.put(word, wordFrequency.getOrDefault(word, 0) + 1);
        }

        return wordFrequency.size();
    }
}

Q4:Write a Java Program to find the duplicate characters in a string.

import java.util.HashSet;
import java.util.Set;

public class DuplicateCharacters {
    public static void main(String[] args) {
        String inputString = "Write a Java Program to find the duplicate characters in a string";
        Set<Character> duplicates = findDuplicateCharacters(inputString);
        System.out.println("Duplicate characters: " + duplicates);
    }

    public static Set<Character> findDuplicateCharacters(String s) {
        Set<Character> charSet = new HashSet<>();
        Set<Character> duplicates = new HashSet<>();

        for (char c : s.toCharArray()) {
            if (charSet.contains(c)) {
                duplicates.add(c);
            } else {
                charSet.add(c);
            }
        }

        return duplicates;
    }
}
