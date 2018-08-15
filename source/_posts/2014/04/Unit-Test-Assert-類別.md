---
title: Unit Test Assert 類別
tags:
  - Unit Test
date: 2014-04-23 17:49:00
---

<div>[Assert 類別](http://msdn.microsoft.com/zh-tw/library/microsoft.visualstudio.testtools.unittesting.assert.aspx)</div>
<div><table border="1" cellpadding="3" cellspacing="1"><tbody><tr><td>AreEqual</td><td>確認兩個指定的物件相等
如果這些物件都不相等，判斷提示就會失敗</td></tr><tr><td>AreNotEqual</td><td>確認兩個指定的物件不相等
如果這些物件都相等，判斷提示就會失敗</td></tr><tr><td>AreSame</td><td>確認兩個指定的物件變數參考相同的物件
如果它們參考不同的物件，判斷提示就會失敗</td></tr><tr><td>AreNotSame</td><td>確認兩個指定的物件變數參考不同的物件
如果它們參考相同的物件，判斷提示就會失敗</td></tr><tr><td>IsTrue</td><td>驗證指定的條件是 true
如果條件為 false，判斷提示就會失敗。</td></tr><tr><td>IsFalse</td><td>驗證指定的條件是 false
如果條件為 true，判斷提示就會失敗</td></tr><tr><td>IsNull</td><td>確認指定的物件是 null
如果它不是 null，判斷提示就會失敗</td></tr><tr><td>IsNotNull</td><td>確認指定的物件不是 null
如果它是 null，判斷提示就會失敗</td></tr><tr><td>IsInstanceOfType</td><td>確認指定的物件是指定之型別的執行個體
如果此型別不在物件的繼承階層架構內，判斷提示就會失敗</td></tr><tr><td>IsNotInstanceOfType</td><td>確認指定的物件不是指定之型別的執行個體
如果此型別位於物件的繼承階層架構內，判斷提示就會失敗</td></tr><tr><td>Fail</td><td>判斷提示失敗，但不檢查任何條件</td></tr><tr><td>Inconclusive</td><td>表示無法驗證判斷提示</td></tr></tbody></table></div>
<div>[CollectionAssert 類別](http://msdn.microsoft.com/zh-tw/library/Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert.aspx)</div>
<div><table border="1" cellpadding="3" cellspacing="1"><tbody><tr><td>AllItemsAreInstancesOfType</td><td>確認指定之集合中的所有項目都是指定之型別的執行個體
如果任何項目的型別不在其繼承階層架構內，判斷提示就會失敗</td></tr><tr><td>AllItemsAreNotNull</td><td>確認指定之集合中的所有項目都不是 null
如果有任何項目是 null，判斷提示就會失敗</td></tr><tr><td>AllItemsAreUnique</td><td>確認指定之集合中的所有項目都是唯一的
如果集合中有任兩個項目相等，判斷提示就會失敗</td></tr><tr><td>AreEqual</td><td>確認兩個指定的集合相等
如果這些集合都不相等，判斷提示就會失敗</td></tr><tr><td>AreNotEqual</td><td>確認兩個指定的集合不相等
如果這些集合都相等，判斷提示就會失敗</td></tr><tr><td>AreEquivalent</td><td>確認兩個指定的集合對等
如果這些集合都不對等，判斷提示就會失敗</td></tr><tr><td>AreNotEquivalent</td><td>確認兩個指定的集合不對等
如果這些集合都對等，判斷提示就會失敗</td></tr><tr><td>Contains</td><td>確認指定的集合包含指定的項目
如果此項目不在集合中，判斷提示就會失敗</td></tr><tr><td>DoesNotContain</td><td>確認指定的集合不包含指定的項目
如果此項目位於集合中，判斷提示就會失敗</td></tr><tr><td>IsSubsetOf</td><td>確認第一個集合是第二個集合的子集</td></tr><tr><td>IsNotSubsetOf</td><td>確認第一個集合不是第二個集合的子集</td></tr></tbody></table></div>
<div>[StringAssert 類別](http://msdn.microsoft.com/zh-tw/library/microsoft.visualstudio.testtools.unittesting.stringassert_methods.aspx)</div>
<div><table border="1" cellpadding="3" cellspacing="1"><tbody><tr><td>Contains</td><td>確認第一個字串包含第二個字串
這個方法會區分大小寫</td></tr><tr><td>StartsWith</td><td>確認第一個字串以第二個字串開始
這個方法會區分大小寫</td></tr><tr><td>EndsWith</td><td>確認第一個字串以第二個字串結束
這個方法會區分大小寫</td></tr><tr><td>Matches</td><td>確認指定的字串符合規則運算式</td></tr><tr><td>DoesNotMatch</td><td>確認指定的字串不符合規則運算式</td></tr></tbody></table></div>
<div>
</div>