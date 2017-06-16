# CI_learn
CI框架学习
1、定义各种常量
SELF:index.php;
BASEPATH:G:/XAMPP/htdoc/sina/testing/system;
FCPATH:G:/XAMPP/htdoc/sina/testing;
SYSDIR:system;
APPPATH:Aplication;

2.引入BASEPATH/core/Codelgniter.php
引入core/Common.php公共函数（todo//各个函数作用）
引入框架常量require(APPPATH.'config/'.ENVIRONMENT.'/constants.php');

$BM =& load_class('Benchmark', 'core');//创建$BM对象，这个类允许您标记点并计算它们之间的时间差。内存消耗也可以显示。
$BM->mark('total_execution_time_start');//记录'total_execution_time_start的时间
$BM->mark('loading_time:_base_classes_start');记录loading_time:_base_classes_start的时间

$EXT =& load_class('Hooks', 'core');//创建Hooks对象

$CFG =& load_class('Config', 'core');//创建Config对象
Config初始化调用构造函数：&get_config；$this->set_item('base_url', $base_url);//$base_url=http://sina.sina.com.cn/testing/

$UNI =& load_class('Utf8', 'core');//创建Utf8对象

$URI =& load_class('URI', 'core');//构造函数：new config对象

$RTR =& load_class('Router', 'core');//构造函数new config对象 new uri对象
如果在index.php中设置了$routing变量，则启动url重写

$OUT =& load_class('Output', 'core');//构造函数：


core/Common.php函数作用

1.funcion load_class($class, $directory = 'libraries', $prefix = 'CI_')
首先判断$_classes数组中有没有改对象，如果有，则return该对象，如果没有
在APP/$directory和system/$directory中查找有没有相应$class，如果有则new，传入$_classes数组,并return 对象

2.function &get_config($replace = array())返回APPPATH.'config/config.php';
