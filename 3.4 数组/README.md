# Array 对象<br />
##创建数组<br />
创建数组的基本方式有两种。第一种是使用Array构造函数，如下面的代码所示。<br /> <br /> 

>> - 空数组 var Obj =  new Array();  <br /> 
>> - 指定长度数组 var Obj = new Array(Size);  <br /> 
>> - 指定元素数组 var Obj = new Array(元素1，元素2，元素3,...,元素N)；  <br /> 
>> - 多维数组 var Obj = new Array([数组1],[数组2],[数组N]) <br /> 

创建数组的第二种方式是使用直接量，如下所示。  <br />

>> - var Obj = [元素1,元素2,...,元素n]

##Array 构造器的属性<br />
###Array.prototype
###Array.isArray ( arg )
isArray 函数需要一个参数 arg，如果参数是个对象并且 class 内部属性是<br />
"Array", 返回布尔值 true；否则它返回 false。采用如下步骤：<br />
    1. 如果 Type(arg) 不是 Object, 返回 false。 <br />
    2. 如果 arg 的 [[Class]] 内部属性值是 "Array", 则返回 true。<br />
    3. 返回 false.<br />   
###Array.length<br />

##基本操作方法<br />
###存取数组元素<br />
>> - 单位数组 数组名[下标索引]<br /> 
>> - 多维数组 数组名 [外层元素下标][内层元素下标] <br /> 

###增加数组元素<br />
>> - 增加数组 使用'数组名[]'指定一个新下标  <br /> 

###删除数组元素<br />
>> - 删除数组 delete 数组名[下标] <br /> 

###遍历数组元素<br />
>> - 遍历数组 使用for循环遍历数组 <br /> 

##数组原型对象的属性 <br />
###Array.prototype.constructor<br />
>> - Array.prototype.constructor 的初始值是标准内置 Array 构造器。<br />

###添加方法<br />
>> - Array.prototype.push ( [ item1 [ , item2 [ , … ] ] ] )  在数组末尾添加数组元素<br />
>> - Array.prototype.unshift ( [ item1 [ , item2 [ , … ] ] ] )  在数组头部添加数组元素<br />
>> - Array.prototype.concat ( [ item1 [ , item2 [ , … ] ] ] ) 当以零或更多个参数 item1, item2, 等等，调用 concat 方法，返回一个新数组，
这个数组包含对象的数组元素和后面跟着的每个参数按照顺序组成的数组元素。

###删除方法<br />
>> - Array.prototype.pop ( )  删除并返回数组的最后一个元素<br />
>> - Array.prototype.shift ( )   删除并返回数组的第一个元素<br />

###子数组方法<br />
>> - Array.prototype.slice (start, end)  slice 方法需要 start 和 end 两个参数，返回一个数组，这个数组包含从第 start个元素到 -- 但不包括 -- 第 end 个元素 ( 或如果 end 是 undefined 就到数组末尾 )。如果 start 为负，它会被当做是 length+start，这里的 length 是数组长度。如果 end 为负，它会被当做是 length+end，这里的 length 是数组长度。<br />
>> - Array.prototype.splice (start, deleteCount ，addElement1， addElement2，... )  返回一个数组，该数组包含原始数组删除的项，会修改原数组
     - 删除：可以删除任意数量的项，只需指定2个参数：[start,deleteCount]。
     - 插入：可以向指定位置插入任意数量的项，只需提供3个参数：[start，deleteCount（0），addElement1，...]
     - 替换：可以向指定位置插入任意数量的项，且同时删除任意数量的项，只需指定3个参数：[start，deleteCount（0），addElement1，...]
###排序方法<br />
>> - Array.prototype.reverse ( ) 重新排列数组元素，以翻转它们的顺序。对象会被当做调用的结果返回。<br />
>> - Array.prototype.sort (comparefn) <br /> 

>>> - 对字符数或数字数组进行排序，默认按字符串比较<br />
>>> - 按数值大小比较需要函数支持，如下所示<br />
```
function compare(a,b){
 		return b - a
}
```

###数组转换
>> - Array.prototype.toLocaleString ( ) 转换为字符串并还回<br />
>> - Array.prototype.toString ( ) 转换为本地字符串并还回<br />
>> - Array.prototype.join (separator) 用指定的分隔符分割数组并转换为字符串<br />

###位置方法
>> - Array.prototype.indexOf ( searchElement [ , fromIndex ] ) indexOf 按照索引的升序比较 searchElement 和数组里的元素们，它使用内部
的严格相等比较算法 (11.9.6)，如果找到一个或更多这样的位置，返回这些位置中第一个索引；否则返回 -1。可选的第二个参数 fromIndex 默认是 0（即搜索整个数组）。如果它大于或等于数组长度，返回 -1，即不会搜索数组。如果它是负的，就把它当作从数组末尾到计算后的 fromIndex 的偏移量。如果计算后的索引小于 0，就搜索整个数组。
>> - Array.prototype.lastIndexOf ( searchElement [ , fromIndex ] ) lastIndexOf 按照索引的降序比较 searchElement 和数组里的元素们，它使用
内部的严格相等比较算法 (11.9.6)，如果找到一个或更多这样的位置，返回这些位置中最后一个索引；否则返回 -1。可选的第二个参数 fromIndex 默认是数组的长度减一（即搜索整个数组）。如果它大于或等于数组长度，将会搜索整个数组。如果它是负的，就把它当作从数组末尾到计算后的 fromIndex 的偏移量。如果计算后的索引小于 0，返回 -1。

###迭代方法
>> - Array.prototype.forEach ( callbackfn [ , thisArg ] ) callbackfn 应该是个函数，它接受三个参数。forEach 按照索引的升序，对数组里存在的每个元素调用一次 callbackfn。callbackfn 只被实际存在的数组元素调用；它不会被缺少的数组元素调用。如果提供了一个 thisArg 参数，它会被当作 this 值传给每个 callbackfn 调用。如果没提供它，用 undefined 替代。调用 callbackfn 时将传入三个参数：元素的值，元素的索引，和遍历的对象。对 forEach 的调用不直接更改对象，但是对 callbackfn 的调用可能更改对象。forEach 处理的元素范围是在首次调用 callbackfn 之前设定的。在 forEach 调用开始后追加到数组里的元素们不会被 callbackfn 访问。如果更改以存在数组元素，forEach 访问这些元素时的值会传给 callbackfn；在 forEach 调用开始后删除的和之前被访问过的元素们是不访问的。
>> - Array.prototype.map ( callbackfn [ , thisArg ] ) callbackfn 应该是个函数，它接受三个参数。map 按照索引的升序，对数组里存在的每个元素调用一次 callbackfn，并用结果构造一个新数组。callbackfn 只被实际存在的数组元素调用；它不会被缺少的数组元素调用。如果提供了一个 thisArg 参数，它会被当作 this 值传给每个 callbackfn 调用。如果没提供它，用 undefined 替代。调用 callbackfn 时将传入三个参数：元素的值，元素的索引，和遍历的对象。对 map 的调用不直接更改对象，但是对 callbackfn 的调用可能更改对象。map 处理的元素范围是在首次调用 callbackfn 之前设定的。在 map 调用开始后追加到数组里的元素们不会被 callbackfn 访问。如果更改以存在数组元素，map 访问这些元素时的值会传给 callbackfn；在 map 调用开始后删除的和之前被访问过的元素们是不访问的。
>> - Array.prototype.filter ( callbackfn [ , thisArg ] ) callbackfn 应该是个函数，它接受三个参数并返回一个可转换为布尔值 true 和false 的值。filter 按照索引的升序，对数组里存在的每个元素调用一次callbackfn，并用使 callbackfn 返回 true 的所有值构造一个新数组。callbackfn只被实际存在的数组元素调用；它不会被缺少的数组元素调用。如果提供了一个 thisArg 参数，它会被当作 this 值传给每个 callbackfn 调用。如果没提供它，用 undefined 替代。调用 callbackfn 时将传入三个参数：元素的值，元素的索引，和遍历的对象。对 filter 的调用不直接更改对象，但是对 callbackfn 的调用可能更改对象。filter 处理的元素范围是在首次调用 callbackfn 之前设定的。在 filter 调用开始后追加到数组里的元素们不会被 callbackfn 访问。如果更改以存在数组元素，filter 访问这些元素时的值会传给 callbackfn；在 filter 调用开始后删除的和之前被访问过的元素们是不访问的。
>> - Array.prototype.every ( callbackfn [ , thisArg ] )callbackfn 应该是个函数，它接受三个参数并返回一个可转换为布尔值 true 和
false 的值。every 按照索引的升序，对数组里存在的每个元素调用一次callbackfn，直到他找到一个使 callbackfn 返回 false 的元素。如果找到这样的
元素，every 马上返回 false，否则如果对所有元素 callbackfn 都返回 true，every 将返回 true。callbackfn 只被数组里实际存在的元素调用；它不会被缺
少的元素调用。如果提供了一个 thisArg 参数，它会被当作 this 值传给每个 callbackfn 调用。如果没提供它，用 undefined 替代。
调用 callbackfn 时将传入三个参数：元素的值，元素的索引，和遍历的对象。对 every 的调用不直接更改对象，但是对 callbackfn 的调用可能更改对象。
every 处理的元素范围是在首次调用 callbackfn 之前设定的。在 every 调用开始后追加到数组里的元素们不会被 callbackfn 访问。如果更改以存在数组元素，
every 访问这些元素时的值会传给 callbackfn；在 every 调用开始后删除的和之前被访问过的元素们是不访问的。every 的行为就像数学量词“所有（for all）”。
特别的，对一个空数组，它返回 true。
>> - Array.prototype.some ( callbackfn [ , thisArg ] ) callbackfn 应该是个函数，它接受三个参数并返回一个可转换为布尔值 true 和
false 的值。some 按照索引的升序，对数组里存在的每个元素调用一次callbackfn，直到他找到一个使 callbackfn 返回 true 的元素。如果找到这样的
元素，some 马上返回 true，否则，some 返回 false。callbackfn 只被实际存在的数组元素调用；它不会被缺少的数组元素调用。
如果提供了一个 thisArg 参数，它会被当作 this 值传给每个 callbackfn 调用。如果没提供它，用 undefined 替代。调用 callbackfn 时将传入三个参数：元素的值，元素的索引，和遍历的对象。对 some 的调用不直接更改对象，但是对 callbackfn 的调用可能更改对象。some 处理的元素范围是在首次调用 callbackfn 之前设定的。在 some 调用开始后追加到数组里的元素们不会被 callbackfn 访问。如果更改以存在数组元素，some 访问这些元素时的值会传给 callbackfn；在 some 调用开始后删除的和之前被访问过的元素们是不访问的。some 的行为就像数学量词“存在（exists）”。特别的，对一个空数组，它返回 false。

###缩小方法
>> - Array.prototype.reduce ( callbackfn [ , initialValue ] ) callbackfn 应该是个函数，它需要四个参数。reduce 按照索引的升序，对数组里存在的每个元素 , 将 callbackfn 作为回调函数调用一次。调用 callbackfn 时将传入四个参数：previousValue（initialValue 的值或上次调用 callbackfn 的返回值），currentValue（当前元素值），currentIndex，和遍历的对象。第一次调用回调函数时，previousValue 和 currentValue 的取值可以是下面两种情况之一。如果为 reduce 调用提供了一个 initialValue，则previousValue 将等于 initialValue 并且 currentValue 将等于数组的首个元素值。如果没提供initialValue，则 previousValue 将等于数组的首个元素值并且currentValue 将等于数组的第二个元素值。如果数组里没有元素并且没有提供initialValue，则抛出一个 TypeError 异常。对 reduce 的调用不直接更改对象，但是对 callbackfn 的调用可能更改对象。reduce 处理的元素范围是在首次调用 callbackfn 之前设定的。在 reduce 调用开始后追加到数组里的元素们不会被 callbackfn 访问。如果更改以存在数组元素，reduce 访问这些元素时的值会传给 callbackfn；在 reduce 调用开始后删除的和之前被访问过的元素们是不访问的。
>> - Array.prototype.reduceRight ( callbackfn [ , initialValue ] ) callbackfn 应该是个函数，它需要四个参数。reduceRight 按照索引的升序，对
数组里存在的每个元素 , 将 callbackfn 作为回调函数调用一次。调用 callbackfn 时将传入四个参数：previousValue（initialValue 的值或上次调用callbackfn 的返回值），currentValue（当前元素值），currentIndex，和遍历的对象。第一次调用回调函数时，previousValue 和 currentValue 的取值
可以是下面两种情况之一。如果为 reduceRight 调用提供了一个 initialValue，则 previousValue 将等于 initialValue 并且 currentValue 将等于数组的最后
一个元素值。如果没提供 initialValue，则 previousValue 将等于数组的最后一个元素值并且 currentValue 将等于数组的倒数第二个元素值。如果数组里没有
元素并且没有提供 initialValue，则抛出一个 TypeError 异常。对 reduceRight 的调用不直接更改对象，但是对 callbackfn 的调用可能更改对象。reduceRight 处理的元素范围是在首次调用 callbackfn 之前设定的。在reduceRight 调用开始后追加到数组里的元素们不会被 callbackfn 访问。如果更改以存在数组元素，reduceRight 访问这些元素时的值会传给 callbackfn；在reduceRight 调用开始后删除的和之前被访问过的元素们是不访问的。

##参考资料：
###ECMA-262-5.1
###JavaScript权威指南
###JavaScript高级程序设计
