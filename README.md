# 26、leetcode434. 字符串中的单词数
解法一：
--  
思路：
--
    使用内置函数。    
代码： 
--
<pre>
/**
 * @author lihe
 * @date 2019/10/21 10:45
 * @descriptor
 */
public class CountSegments_434 {
    public int countSegments(String s) {
        String trimmed = s.trim();
        if (trimmed.equals("")) {
            return 0;
        }
        return trimmed.split("\\s+").length;
}
    public static void main(String[] args) {
        String s = " hello, world a f";
        int i = countSegments2(s);
        System.out.println(i);
    }
}
</pre>
解法二：
--  
思路：
--
    原地法： 计算单词的数量，就等同于计数单词开始的下标个数。因此，只需要定义好下标的条件，就可以遍历整个字符串，检测每个下标。定义如下：若该下标前为空格（或者为初始下标），且自身不为空格，则其为单词开始的下标。该条件可以以常数时间检测。最后，返回满足条件的下标个数。  
代码： 
--
<pre>
/**
 * @author lihe
 * @date 2019/10/21 10:45
 * @descriptor
 */
public class CountSegments_434 {
    public static int countSegments(String s) {
        s = s.trim();
        int count = 1;
        for (int i = 0; i < s.length(); i++) {
            if(s.charAt(i-1) == ' ' && s.charAt(i) != ' '){
                count ++;
            }
        }
        return count;
    }
    public static void main(String[] args) {
        String s = " hello, world a f";
        int i = countSegments2(s);
        System.out.println(i);
    }
}
</pre>
解法三：
--  
思路：
--
    双指针法： 在每次进入循环的时候，保证指针i是指向一个单词的开头，而再对i处理完毕后，保证指针j是指向一个单词的结尾后的空格。因此在不越界的情况下，上述的i和j两个指针其实就能完成对一个单词的统计。  
代码： 
--
<pre>
/**
 * @author lihe
 * @date 2019/10/21 10:45
 * @descriptor
 */
public class CountSegments_434 {
  public static int countSegments2(String s) {
        int i = 0,j = 0,count = 0;
        while(i < s.length()){
            while(i < s.length() && s.charAt(i) == ' ')i++;
            j = i;
            if(j < s.length()){
                while(j < s.length() && s.charAt(j) != ' ')j++;
                i = j + 1;
                count ++;
            }
        }
        return count;
    }
    public static void main(String[] args) {
        String s = " hello, world a f";
        int i = countSegments2(s);
        System.out.println(i);
    }
}
</pre>
