为什么匿名内部类，局部内部类、以及Lambda访问的外部变量需要是fianl类型的



本质就一点，因为当外部变量由于方法结束而由GC回收时，匿名内部类，局部内部类和lambada表达式中的对该变量的复制（是以复制方式传入的）不会消失，并且匿名内部类等也不会立即结束（由于线程运行的原因），这时候如果不用final定义该类（或者从事实意义上没有满足final），就有可能导致值被修改，这样就会导致内外的值不同。