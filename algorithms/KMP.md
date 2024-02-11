### ELI5
- Search for reoccurring patterns in O(n + m) time, especially useful if the pattern has reoccurring sub-patterns

### Steps
- Pre-compute LPS ("Longest Prefix Suffix")
    - Each position of the LPS array corresponds to a substring of the pattern, i.e. every single prefix of the pattern
    - Deduce the length* of the longest proper prefix that is also a suffix for the given substring
- Search

### Characteristics
- LPS
    - 1st position is always 0 because there is no proper prefix for substring of length 1

### Implementation
```
private static int[] computeLPS(int[] pattern) {
    int[] lps = new int[pattern.length];
    int length = 0;
    int i = 1;
    
    lps[0] = 0; // LPS of the first character is always 0
    
    while (i < pattern.length) {
        if (pattern[i] == pattern[length]) {
            length++;
            lps[i] = length;
            i++;
        } else if (pattern[i] != pattern[length]) {
            if (length == 0) {
                lps[i] = 0;
                i++;
            } else if (length != 0) {
                length = lps[length - 1];
            }
        }
    }
    return lps;
}
    
public static void KMPSearch(int[] pattern, int[] array) {
    int[] lps = computeLPS(pattern);
    int i = 0; // index for array[]
    int j = 0; // index for pattern[]
    
    while (i < array.length) {
        if (pattern[j] == array[i]) {
            j++;
            i++;
        } else if (i < array.length && pattern[j] != array[i]) {
            if (j == 0) {
                i++;
            } else if (j != 0) {
                j = lps[j - 1];
            }
        }

        if (j == pattern.length) {
            System.out.println("Found pattern at index " + (i - j));
            j = lps[j - 1];
        }
    }
}
    
public static void main(String[] args) {
    int[] array = {1, 2, 3, 4, 1, 2, 3, 4, 5};
    int[] pattern = {1, 2, 3};
    
    KMPSearch(pattern, array);
}
```