# Powerformer React Style Guide() {

*A mostly reasonable approach to Coding*

> **注意**: 一般的变量命名会以涵盖标题为主，涉及四个值得变量命名会使用`top, right, bottom, left`, 涉及少于四个或者大于四个的变量命名会使用`first, second ...`。

## 目录 <a id="table-of-contents"></a>

  1. [代码风格](#code-style)

## 代码风格 <a id="code-style"></a>

  - [1.1](#code-style-location) 组件中，所有的变量或方法必须得在某一处一致引用,在结尾一致导出。

    ```javascript
    // bad

    render () {
      return (
        <div>
          <p>{this.props.content}</p>
          <button onClick={this.props.handleClick}>first</button>
        </div>
      )
    }

    // good
    render () {
      const { content, handleClick } = this.props;

      return (
        <div>
          <p>{content}</p>
          <button onClick={handleClick}>first</button>
        </div>
      )
    }
    ```

  - [1.2](#dirName) 文件 / 文件夹名一律首字母大写，驼峰式命名。

    ```markdown
    // bad
    Components
      - courseOutline
       - App.js
      
    // also bad
    Components
      - Course
        - courseOutline.js

    // good
    Components
      - CourseOutline
       - App.js
    
    // also good
    Components
      - Course
        - CourseOutline.js
    ```

  - [1.3](#static-name) 项目中，静态资源 / 测试 文件夹名使用小写字母。

    ```javascript
    // image
    - images
      - MyPicture.png

    // css
    - css
      - MyStyle.css

    // test
    - tests
      - MyTest.test.js

    - __tests__
      - MyTest.js
    ```

}