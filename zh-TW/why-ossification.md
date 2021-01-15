# 協定僵化 ( ossification )

網際網路（ Internet ）是由多個網路互相相連而成。為了保證網際網路正常運作，我們需要在網際網路各處搭建各種設備。這些在網際網路上分佈式架設的設備被稱為中間設備（ middle-box ）。傳統網際網路傳輸中，兩個端點之間的中間設備肩負著網路資料的傳輸。

這些中間設備有很多，各式各樣的用途和目的，但我可以說，這些設備被放置在該位置是因為有人認為它一定要在那個位置才能讓網路的工作完成。

中間設備的綜合用途：在網路間轉送封包（ 路由 ）、阻擋惡意流量、網路位址轉換（ NAT ）、提升性能、監控流量...等等。

為了完成這些目的，這些設備必須了解網路以及它們所要監視或修改的協定。它們為此依賴於一些程式，一些很少更新或升級的程式。

儘管它們是使網路連在一起的關鍵元素，但它們通常也跟不上最新的技術。網路核心的更新速度通常不如世界上的客戶端或伺服器快。

所以當這些設備能夠決定經過的流量是否安全或合格時，就有問題了。在這些設備部署之後的一段時間裡，協定有了新的功能或更新。
而在這些設備引入（ 理解 ）這些新功能之前，它們會認為這種特性的封包是非法、惡意的，於是這些流量將直接被丟棄，或是拖延直到用戶不再想使用這些新的功能。

這種現象我們稱之為 "協定僵化"

TCP 的更改也容易僵化：客戶端和遠程伺服器之間的某些中間設備會發現未知的 TCP 選項並阻止此類連接，因為它們不知道這些選項是什麼。如果中間設備監測了協定的實作細節，它們會學習到協定的典型行為，一段時間後，這些行為將無法更改。

盡可能的將通信加密是對抗僵化的唯一有效手段，加密可以防止中間設備看到協定傳輸的絕大部分內容。