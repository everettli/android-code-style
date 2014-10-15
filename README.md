android code style
==================
#Android 编程规范
本编程规范参考Code Style Guidelines for Contributors整理，如有错误，欢迎完善。
##一 注释规范
###1. 类、接口注释的内容
1. 用途。开发人员使用某个类/接口之前，需要知道采用该类/接口的用途
2. 开发维护的日志。一个有关于该类/接口的维护记录：时间、作者、摘要。
Eclipse 代码格式化：
位置：
`Window` › `Preferences` › `Java` › `Code Style` > `Code Template` > `Code` > `New Java files`

内容：
```
${filecomment}
${package_declaration}
/** 
 * 类说明：
 * @author  Liucd
 * @date    ${date}
 * @version 1.0
 */ 
${typecomment}
${type_declaration}
```

###2. 方法注释的内容（要求所有的public方法都有注释,多一个public方法就多一份维护的责任）
1. 该方法是做什么的。
2. 传入什么样的参数给这个方法。@param
3. 异常处理。@throws
4. 这个方法返回什么。@return

```
/** 
 * 方法说明 
 * @param cityId 城市ID
 * @param …
 * @throws InvalidParamException
 * @return 返回。。。
 */
 ```

##二 命名规范
   命名规范的目的是使程序更易读。它们也可以提供一些有关标识符功能的信息，以助于理解代码，不论它是一个常量、包、还是类。
应该尽量做到以下几点：
1. 使用完整的英文描述来命名；避免命名超长（15 个字符以内比较好）；
2. 避免相似的命名，例如：persistentObj 和persistentObjs 不要一起使用；anSqlStmt 和anSQLStmt 不要一起使用；
3. 慎用缩写，如果要用到缩写，则按照缩写规则使用缩写，例如：No.代表number 数字，ID.代表identification标示。

下面分类介绍命名规范。
###1. 包
包名全小写
import com.aispeech.common

###2. 类/接口
大小写字母混合组成，头字母大写，名字要有意义。若不能说明功能，考虑增加类名称长度，一定要让其他人能够通过这个类知道这个类的主要用途。需要注意的几点：
  * 基类使用Base开头，如BaseActivity等。
  * 抽象类使用Abstract开头，如AbstractAdapter等。
  * 接口用大写I开头。
  * 子类或者实现类，要说明主要用途。不同子类的名字要能够体现区别。

###3. 方法
方法名字是一个动词，大小写字母混合组成，第一个单词的首字母小写，其后单词的首字母大写，名字要有意义。
run();
getBackground();

###4. 变量、参数
变量用大小写混合的方式，第一个单词的首字母小写，其后单词的首字母大写。变量名不应以下划线或$符号开头，尽管这在语法上是允许的。
变量名应简短且富于描述。变量名的选用应该易于记忆，即，能够指出其用途。尽量避免单个字符的变量名，除非是一次性的临时变量。临时变量通常被取名为i，j，k，m 和n，它们一般用于整型；c，d，e，它们一般用于字符型。
公共空间的命名：
```
TextView txtPrice
ImageView imgAvatar
EditText editUserName
ListView listView
GridView gridView
Button btnLogin // loginButton
Bitmap bmpAvatar
RelativeLayout/ LinearLayout… layout***
```

###5. 集合、数组
应该从命名中体现其复数的含义，例如加后缀s或前缀some，名字要有意义。
```
customers;
postedMessages;
someCustomers;
someItems;
```
###6. 域(Field)命名
成员变量以m开头，这个要求非强制。在Android源码中，大多数代码中的成员变量是m开头的，这个习惯是从C/C++演变而来的，m代表member，表示这个变量是一个成员变量。
对于局部变量不能使用m开头（变量名称为单字母m除外），如：
```
public void foo(){ 
    int mProtected = 0; // Too Bad
    TextView mTxtName = ()… // forbidden.
}
```
静态域命名以s开头。
其他字段以小写字母开头。
public static final 字段(常量) 全部大写，并用下划线连起来。
例子：
```
public class MyClass{
    public static final int SOME_CONSTANT = 42;
    public int publicField;
    private static MyClass sSingleton;
    int mPackagePrivate;
    private int mPrivate;
    protected int mProtected;
}
```
####7. 资源文件命名规范 
**res/layout目录下文件：**
统一用小写和下划线"_"组合命名，严格使用英文单词，不能出现拼音和单词混排的情况（若无对应英文单词，也可以使用拼音，但是要尽量避免）。另外，建议xml文件加个前缀以便区分，

```bash
contentview命名：activity_功能模块.xml
 例如：activity_main.xml、activity_more.xml
Dialog命名：dialog_描述.xml
 例如：dlg_hint.xml
PopupWindow命名：ppw_描述.xml
 例如：ppw _info.xml
列表项命名listitem_描述.xml
 例如：listitem_city.xml
包含项：include_模块.xml
 例如：include_head.xml、include_bottom.xml
```

**res/drawable目录下文件：**
统一用小写加下划线“_”组合命名，严格使用英文单词，不能出现拼音和单词混排的情况（若无对应英文单词，也可以使用拼音，但是要尽量避免）。另外，每个资源文件最好加个前缀以便区分，如：
btn_submit_nor.png
btn_submit_press.png;
或者，使用功能模块来区分素材，如：
search_btn_submit_select.png,
search_btn_submit_unselect.png;

默认的drawable中的Selector的后缀：```btn_back_selector.xml```


**drawable资源前缀对照表：**

| 前缀 |说明 |
|:----:|:-------------|
| ic   | --icon, 主要用于布局和子布局的图标 |
| bg   | --background, 主要用于布局的背景   |
| btn  | --button, 主要用于可点击的view     |


**图片资源后缀对照表：**

| 后缀 |说明 |
|:----:|:-------------|
| nor   | 表示普通态 |
| hl   | 表示高亮态  |
| press  | 表示按下态 |
| select | 表示view被选中 |
| unselect | 表示view没有被选中 |


布局文件中的id命名规范：
统一用小写加下划线组合命名，前缀使用txt/img/btn/layout/list等，分别代表TextView、ImageView、Button、Layout、ListView，命名如下所示：

```xml
android:id=”@+id/txt_title”
android:id=”@+id/img_right_arrow”
android:id=”@+id/layout_titlebar”
```

