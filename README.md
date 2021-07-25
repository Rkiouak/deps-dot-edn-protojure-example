```clojure
$ clj
Clojure 1.10.0
user=> (require '[com.example.addressbook.Greeter.client :as client])
nil
user=> (require '[com.example.addressbook.Greeter.server :as server])
nil
user=> (require '[server :as main])
SLF4J: No SLF4J providers were found.
...
nil
user=> (main/-main)

Creating your server...
{:io.pedestal.http/port 8080, :io.pedestal.http/host "localhost", :io.pedestal.http/type #object[protojure.pedestal.core$config 0x78b5f3c6 "protojure.pedestal.core$config@78b5f3c6"], :io.pedestal.http/start-fn #object[protojure.pedestal.core$config$fn__8220 0x5e409078 "protojure.pedestal.core$config$fn__8220@5e409078"], :env :prod, :io.pedestal.http/interceptors [#Interceptor{:name :io.pedestal.http/log-request} #Interceptor{:name :io.pedestal.http/not-found} #Interceptor{:name :io.pedestal.http.ring-middlewares/content-type-interceptor} #Interceptor{:name :io.pedestal.http.route/query-params} #Interceptor{:name :io.pedestal.http.route/path-params-decoder} #Interceptor{:name :io.pedestal.http.route/method-param} #Interceptor{:name :io.pedestal.http.secure-headers/secure-headers} #Interceptor{:name :io.pedestal.http.route/router}], :io.pedestal.http/routes #{["/about" :get [#Interceptor{:name :io.pedestal.http.body-params/body-params} #Interceptor{:name :io.pedestal.http/html-body} service/about-page]] ["/" :get [#Interceptor{:name :io.pedestal.http.body-params/body-params} #Interceptor{:name :io.pedestal.http/html-body} service/home-page]] ["/com.example.addressbook.Greeter/Hello" :post [#Interceptor{} #Interceptor{:name :io.pedestal.http.body-params/body-params} #Interceptor{:name :io.pedestal.http/html-body} #Interceptor{:name :protojure.pedestal.interceptors.grpc-web/proxy} #Interceptor{:name :protojure.pedestal.interceptors.grpc/interceptor} #Interceptor{:name :com.example.addressbook.Greeter/Hello-handler}] :route-name :com.example.addressbook.Greeter/Hello-handler]}, :io.pedestal.http/server #object[io.undertow.Undertow 0x611f82a8 "io.undertow.Undertow@611f82a8"], :io.pedestal.http/chain-provider #object[protojure.pedestal.core$provider 0x51f39482 "protojure.pedestal.core$provider@51f39482"], :io.pedestal.http/stop-fn #object[protojure.pedestal.core$config$fn__8222 0x60f66b9 "protojure.pedestal.core$config$fn__8222@60f66b9"], :protojure.pedestal.core/handler #object[protojure.pedestal.core$provider$reify__8213 0x5c16f550 "protojure.pedestal.core$provider$reify__8213@5c16f550"]}
user=> (use 'protojure.grpc.client.providers.http2)
...
nil
user=> @(client/Hello @(connect {:uri (str "http://localhost:" 8080)}) {:name "John Doe"})
#com.example.addressbook.HelloResponse-record{:message "Hello, John Doe"}
```