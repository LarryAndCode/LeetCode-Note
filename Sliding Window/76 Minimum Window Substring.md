```java
class Solution {
  public String minWindow(String s, String t) {
      if(s.length()==0) return "";
      int d = Integer.MAX_VALUE;
      int[] alphabet = new int[128];
      for(char c:t.toCharArray()) alphabet[c]++;
      int start = 0, len = s.length(), counter = t.length(), head=0;
      for(int end = 0; end<len; end++){
          if(alphabet[s.charAt(end)]-- > 0) counter--;
          while(counter==0){
              if(end-start+1<d){
                  head = start;
                  d=end-start+1;
              }
              if(alphabet[s.charAt(start)]++ == 0) counter++;
              start++;
          }
      }
      return d==Integer.MAX_VALUE? "" : s.substring(head, head+d);
  }
}
```