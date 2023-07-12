# Sort a String

{% embed url="https://practice.geeksforgeeks.org/problems/sort-a-string2943/1" %}





```java
//User function Template for Java
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
        
        StringBuilder answer = new StringBuilder();
        for (int i = abc.length - 1; i >= 1; i--) {
            if (abc[i - 1] < abc[i]) {
                answer.append((char) (i + 96));
                abc[i]--;
            }
        }
        
        return answer.reverse().toString();
    }
}

```



