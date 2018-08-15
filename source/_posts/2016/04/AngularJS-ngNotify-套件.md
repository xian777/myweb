---
title: AngularJS ngNotify 套件
tags:
  - AngularJS套件
date: 2016-04-08 17:37:00
---

# 必要條件

*   IE9+*   AngularJS
*   不需要JQuery

# 安裝指令

    <span class="hljs-comment">bower</span> <span class="hljs-comment">install</span> <span class="hljs-comment">ng</span><span class="hljs-literal">-</span><span class="hljs-comment">notify</span> <span class="hljs-literal">-</span><span class="hljs-literal">-</span><span class="hljs-comment">save</span>
    <span class="hljs-comment">npm</span> <span class="hljs-comment">install</span> <span class="hljs-comment">ng</span><span class="hljs-literal">-</span><span class="hljs-comment">notify</span> <span class="hljs-literal">-</span><span class="hljs-literal">-</span><span class="hljs-comment">save</span>`</pre>

    # CDN
    <pre class="prettyprint">`<span class="hljs-label">http:</span>//cdn<span class="hljs-preprocessor">.jsdelivr</span><span class="hljs-preprocessor">.net</span>/angular<span class="hljs-preprocessor">.ng</span>-notify/<span class="hljs-number">0.8</span><span class="hljs-number">.0</span>/ng-notify<span class="hljs-preprocessor">.min</span><span class="hljs-preprocessor">.js</span>
    <span class="hljs-label">http:</span>//cdn<span class="hljs-preprocessor">.jsdelivr</span><span class="hljs-preprocessor">.net</span>/angular<span class="hljs-preprocessor">.ng</span>-notify/<span class="hljs-number">0.8</span><span class="hljs-number">.0</span>/ng-notify<span class="hljs-preprocessor">.min</span><span class="hljs-preprocessor">.css</span>`</pre>

    # 用法
    app.js
    <pre class="prettyprint">`(<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">()</span> {</span>
        <span class="hljs-comment">// 載入模組</span>
        angular
            .module(<span class="hljs-string">'myApp'</span>, [<span class="hljs-string">'ngNotify'</span>])
            .run(ngNotifyConfig);

        <span class="hljs-comment">// 全域設定</span>
        ngNotifyConfig.$inject = [<span class="hljs-string">"ngNotify"</span>];
        <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">ngNotifyConfig</span><span class="hljs-params">(ngNotify)</span> {</span>
            ngNotify.config({
                theme: <span class="hljs-string">'pure'</span>,
                position: <span class="hljs-string">'bottom'</span>,
                duration: <span class="hljs-number">3000</span>,
                type: <span class="hljs-string">'info'</span>,
                sticky: <span class="hljs-literal">false</span>,
                button: <span class="hljs-literal">true</span>,
                html: <span class="hljs-literal">false</span>
            });
        }
    })();`</pre>IndexController.js
    <pre class="prettyprint">`(<span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">()</span> {</span>
        angular
            .module(<span class="hljs-string">"myApp"</span>)
            .controller(<span class="hljs-string">"IndexController"</span>, IndexController);

        IndexController.$inject = [<span class="hljs-string">"ngNotify"</span>];
        <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-title">IndexController</span><span class="hljs-params">(ngNotify)</span> {</span>
            <span class="hljs-keyword">var</span> vm = <span class="hljs-keyword">this</span>;

            <span class="hljs-comment">// 通知1</span>
            vm.Notify1 = <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">()</span> {</span>
                <span class="hljs-comment">// 呼叫set函式來Notify, 預設為info type</span>
                ngNotify.set(<span class="hljs-string">'Your notification message goes here!'</span>);
            }

            <span class="hljs-comment">// 通知2</span>
            vm.Notify2 = <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">()</span> {</span>
                <span class="hljs-comment">// 可用第二個參數來指定Notify Type</span>
                ngNotify.set(<span class="hljs-string">'Your error message goes here!'</span>, <span class="hljs-string">'error'</span>);
            }

            <span class="hljs-comment">// 呼叫時使用額外的設定值</span>
            vm.Notify3 = <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">()</span> {</span>
                <span class="hljs-comment">// 獨立設定值</span>
                ngNotify.set(<span class="hljs-string">"Your individual message."</span>, {
                    theme: <span class="hljs-string">'pure'</span>,
                    position: <span class="hljs-string">'bottom'</span>,
                    duration: <span class="hljs-number">3000</span>,
                    type: <span class="hljs-string">'info'</span>,
                    sticky: <span class="hljs-literal">false</span>,
                    button: <span class="hljs-literal">false</span>,
                    html: <span class="hljs-literal">true</span>
                });

            }

            <span class="hljs-comment">// 關閉通知時呼叫call back函式    </span>
            vm.NotifyCallBack = <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">()</span> {</span>
                <span class="hljs-keyword">var</span> callback = <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">()</span> {</span> };
                <span class="hljs-comment">// 第三個參數為call back函式</span>
                ngNotify.set(<span class="hljs-string">'This message has a callback.'</span>, {}, callback);
            }

            <span class="hljs-comment">// 自訂顯示通知的容器</span>
            vm.NotifyTarget = <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">()</span> {</span>
                ngNotify.set(<span class="hljs-string">'This message has a specific container!'</span>, {
                    target: <span class="hljs-string">'#new-container'</span>
                });
            }

            <span class="hljs-comment">// 關閉通知</span>
            vm.CloseNotify = <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">()</span> {</span>
                ngNotify.dismiss();
            }

        }
    })();

# 設定值

*   theme: string - 指定使用樣式
    *   pure(default)
    *   prime
    *   pastel
    *   pitchy
*   type: string - 通知類別
    *   info(default)
    *   error
    *   success
    *   warn
    *   grimace
*   position: string - 顯示的位置
    *   bottm(default)
    *   top
*   duration: int - 顯示通知的持續時間毫秒數
*   sticky: bool - 是否持續顯示, 預設為false, 設為true時將不理會duration設定值
*   button: bool - 是否顯示關閉按鈕, 預設為true
*   target: string - 用來指定要顯示通知的容器名稱
*   html: bool - 需要引用angular-sanitize模組才能生效html格式的提示訊息

# 函式定義

*   set(message, type|config, callback)
    *   呼叫提示訊息
*   config(options)
    *   設定參數
*   dismiss()
    *   手動關閉通知, 當sticky設為true且button設為false時使用
*   addType(name, class)
    *   自訂通知類別
*   addTheme(name, class)
    *   自訂顯示樣式

# 相關連結
[ng-notify Live Demo](http://matowens.github.io/ng-notify/#demo "ng-notify Live Demo")
[ng-notify GitHub](https://github.com/matowens/ng-notify/blob/master/README.md "ng-notify GitHub")