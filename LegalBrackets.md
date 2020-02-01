## 题目

给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

有效字符串需满足：

    左括号必须用相同类型的右括号闭合。
    左括号必须以正确的顺序闭合。

示例 1:

输入: "()"
输出: true

示例 2:

输入: "()[]{}"
输出: true

示例 3:

输入: "(]"
输出: false

示例 4:

输入: "([)]"
输出: false

示例 5:

输入: "{[]}"
输出: true

## 思路1

遍历数组找到右括号，然后从此位置向前遍历，如果遇到左括号，就说明有一对匹配，让这一对变空格。结束后再遍历数组如果没有发现括号说明括号完全匹配。

## 代码

```c
#include<stdio.h>
#include<string.h>
int main(){
        char a[100];
        gets(a);
        int n=0;
        n=strlen(a);
        for(int i=0;i<n;i++){
                if(a[i]==')'){
                        for(int j=i-1;j>=0;j--){
                                if(a[j]=='('){
                                        a[i]=' ';
                                        a[j]=' ';
                                        break;
                                }
                        }
                }
                else if(a[i]==']'){
                        for(int j=i-1;j>=0;j--){
                                if(a[j]=='['){
                                        a[i]=' ';
                                        a[j]=' ';
                                        break;
                                }
                        }
                }
                else if(a[i]=='}'){
                        for(int j=i-1;j>=0;j--){
                                if(a[j]=='{'){
                                        a[i]=' ';
                                        a[j]=' ';
                                        break;
                                }
                        }
                }
        }
        int k=0;
        for(int i=0;i<n;i++){
                if(a[i]=='('||a[i]==')'||a[i]=='['||a[i]==']'||a[i]=='{'||a[i]=='}'){
                        k=0;
                        break;
                }
                else{
                        k=1;
                }
        }
        if(k==0){
                printf("0");
        }
        else if(k==1){
                printf("1");
        }

        return 0;
}
```

## 思路

用栈来解决问题， 遇到左括号入栈，遇到右括号和栈顶元素比较，若不匹配或栈空，直接返回０。
 最后若栈非空，返回０，否则返回１。 

## 代码

```c
bool isValid(char * s){
    if(!s || s[0] == "")
        return 1;
    char* stk = (char*)malloc(strlen(s));
    int top = -1;
    int i;
    for(i = 0; s[i] != '\0'; i++){
        switch(s[i]){
            case '(':
            case '[':
            case '{':
                stk[++top] = s[i];
                break;
            case ')':
                if(top < 0 || stk[top--] != '(')
                    return 0;
                break;
            case ']':
                if(top < 0 || stk[top--] != '[')
                    return 0;
                break;
            case '}':
                if(top < 0 || stk[top--] != '{')
                    return 0;
                break;
        }
    }
    if(top >= 0)
        return 0;   
    return 1;
}
```

