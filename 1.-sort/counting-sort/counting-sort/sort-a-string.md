# Sort a String

{% embed url="https://practice.geeksforgeeks.org/problems/sort-a-string2943/1" %}



> time: O(n)

> space: O(1), alphabet characters are 26

```java
class Solution 
{ 
    String sort(String s) 
    {
        // code here
        int abc[] = new int[27]; 
        // System.out.println(abc.toString());
        
        for (int i = 0; i < s.length(); i++) { 
            int c = s.charAt(i) - 96; 
            abc[c] += 1; 
        } 
        
        for (int i = 1; i < abc.length; i++) { 
            abc[i] = abc[i - 1] + abc[i]; 
            // System.out.println(i + " " + abc[i]); 
        } 
        
        char answer[] = new char[s.length()];
        for (int i = 0; i < s.length(); i++) {
            int num = s.charAt(i) - 96;
            int index = abc[num];
            answer[index - 1] = (char) (num + 96);
            abc[num]--;
        }
        
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < answer.length; i++) {
            sb.append(answer[i]);
        }
        
        return sb.toString();
    }
}

```



