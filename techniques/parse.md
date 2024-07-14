### Placeholder parsing method
- Just found the solution to this parsing method pretty clean, we can try to apply this structure universally
- https://leetcode.com/problems/number-of-atoms/description/?envType=daily-question&envId=2024-07-14

```
class Solution {
    public String countOfAtoms(String formula) {
        Stack<Map<String, Integer>> stack = new Stack<>();
        stack.push(new HashMap<>());

        int index = 0;

        while (index < formula.length()) {
            if (formula.charAt(index) == '(') {
                stack.push(new HashMap<>());
                index++;
            } else if (formula.charAt(index) == ')') {
                Map<String, Integer> curMap = stack.pop();
                index++;
                StringBuilder multiplier = new StringBuilder();
                while (index < formula.length() && Character.isDigit(formula.charAt(index))) {
                    multiplier.append(formula.charAt(index));
                    index++;
                }
                if (multiplier.length() > 0) {
                    int mult = Integer.parseInt(multiplier.toString());
                    for (String atom : curMap.keySet()) curMap.put(atom, curMap.get(atom) * mult);
                }
                for (String atom : curMap.keySet()) stack.peek().put(atom, stack.peek().getOrDefault(atom, 0) + curMap.get(atom));
            } else {
                StringBuilder curAtom = new StringBuilder();
                curAtom.append(formula.charAt(index));
                index++;
                while (index < formula.length() && Character.isLowerCase(formula.charAt(index))) {
                    curAtom.append(formula.charAt(index));
                    index++;
                }
                StringBuilder curCount = new StringBuilder();
                while (index < formula.length() && Character.isDigit(formula.charAt(index))) {
                    curCount.append(formula.charAt(index));
                    index++;
                }
                int count = curCount.length() > 0 ? Integer.parseInt(curCount.toString()) : 1;
                stack.peek().put(curAtom.toString(), stack.peek().getOrDefault(curAtom.toString(), 0) + count);
            }        
        }

        TreeMap<String, Integer> atomFreqMap = new TreeMap<>(stack.peek());
        StringBuilder sb = new StringBuilder();
        for (String atom : atomFreqMap.keySet()) {
            sb.append(atom);
            if (atomFreqMap.get(atom) > 1) sb.append(atomFreqMap.get(atom));
        }

        return sb.toString();
    }
}
```