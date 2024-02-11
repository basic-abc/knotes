### Debugging
- Set a boolean debug as a private variable to open/close logs
  - If you anticipate more than 1 level, use int for 0 (low) - 4 (high)
```
int debug = 4 // Only see errors

if (debug <= 1) {
  System.out.println("[DEBUG]");
}
if (debug <= 2) {
  System.out.println("[INFO]");
}
if (debug <= 3) {
  System.out.println("[WARN]");
}
if (debug <= 4) {
  System.out.println("[ERROR]");
}
```

### Unit tests
- Set a boolean test variable to invoke a suite for helper functions
```
boolean test = true;

public int jobScheduling(int[] startTime, int[] endTime, int[] profit) {
    if (test) {
        runTests();
        return -1;
    }
    ...
}

private void runTests() {
    testBinarySearchJobIndex();
    System.out.println("Test cases passed!");
}

private void testBinarySearchJobIndex() {
    List<int[]> jobs = List.of(
        new int[] { 1, 3, 50 },
        new int[] { 2, 4, 10 },
        new int[] { 3, 6, 70 },
        new int[] { 3, 5, 40 }
    );

    int expected = 2;
    int next = binarySearchJobIndex(0, jobs);
    if (next != expected) throw new Error("#1 expected / res: " + expected + " / " + next);

    expected = 4;
    next = binarySearchJobIndex(3, jobs);
    if (next != expected) throw new Error("#2 expected / res: " + expected + " / " + next);

    expected = 4;
    next = binarySearchJobIndex(1, jobs);
    if (next != expected) throw new Error("#3 expected / res: " + expected + " / " + next);
}
```