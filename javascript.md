# Powerformer JavaScript Style Guide() {

*A mostly reasonable approach to Coding*

## 目录

  1. [代码风格](#code-style)
  2. [字符串](#String)

## 代码风格

  - [1.1](code-style-indent) 语句块内每行代码缩进`4`个空格.

    ```javascript
    // bad
    function heros() {
      if (x) {
        return x;
      } else {
        return y;
      }
    }

    // good
    function heros() {
        if (x) {
            return x;
        } else {
            return y;
        }
    }
    ```
    
  - [1.2](code-style-limit-row) 每行代码不超过`119`个字符.

    ```javascript
    // bad
    const myBadDream = "Lorem ipsum dolor sit amet consectetur adipisicing elit. Officiis dicta maxime at ratione assumenda, quos, asperiores odit deleniti quia quidem atque quo tempore error a nihil impedit excepturi aliquid nemo?";

    // good
    const myGoodDream = "Lorem ipsum dolor sit amet consectetur adipisicing elit. \
                Officiis dicta maxime at ratione assumenda, quos, asperiores odit \
                deleniti quia quidem atque quo tempore error a nihil impedit      \
                excepturi aliquid nemo?";
    ```
  
## 字符串

  - [2.1](string-quote-style) 静态字符串一律使用单引号，不使用双引号。动态字符串使用反引号

    ```javascript
    // bad
    const staticString = "foobar";

    // good
    const staticString = 'foobar';
    const dynamicString = `foo${staticString}bar`;
    ```
};