# JWTSpringBootDemo

<h2><span id="How_to_test_the_JWT_security_enabled_Application"><span id="How_to_test_the_security_enabled_Application" style="color: #000080;">How to test the JWT security enabled Application ?</span></span></h2>

<p>Although the word ‘testing’ looks very easy to a developer but it is equally important as it provides the result of our implementation on the whole. Therefore, follow the steps given below:</p>

<h3><span id="1_Register_User_through_a_REST_call_using_Postman"><span style="color: #000080;">1) Register User through a REST call using Postman</span></span></h3>

<p>Enter URL <span style="background-color: #ccffff;">http://localhost:8080/user/saveUser</span> in Postman, select POST method, then Select Body&gt;Raw&gt;JSON respectively. Now paste below JSON data and then click on ‘Send’ button.</p>

<p><span style="background-color: #ccffff;">{</span><br>
<span style="background-color: #ccffff;">“username”: “ds2525”,</span><br>
<span style="background-color: #ccffff;">“password”: “donotforgetme”,</span><br>
<span style="background-color: #ccffff;">“email”: “ds2525@gmail.com”,</span><br>
<span style="background-color: #ccffff;">“roles”: [“Admin”,”Manager”]</span><br>
<span style="background-color: #ccffff;">}</span></p>

<p>You should get the below response :</p>
<p>output on Postman : User with id ‘1’ saved succssfully!</p>

<h3><span id="2_Login_as_a_User_to_generate_token"><span style="color: #000080;">2) Login as a User to generate token</span></span></h3>

<p>Enter URL <span style="background-color: #ccffff;">http://localhost:8080/user/loginUser</span> in Postman, select POST method, then Select Body&gt;Raw&gt;JSON respectively. Now paste below JSON data and then click on ‘Send’ button.</p>

<p>{<br>
“username”: “ds2525”,<br>
“password”: “donotforgetme”,<br>
}</p>

<p>You should get the below response :</p>

<div class="code-embed-wrapper"> <div class="code-embed-infos"> <span class="code-embed-name">Output</span> </div> <pre class=" code-embed-pre line-numbers language-css" data-start="1" data-line-offset="0" style="counter-reset: linenumber 0;"><code class=" code-embed-code language-css"><span class="token punctuation">{</span>
<span class="token string">"token"</span><span class="token punctuation">:</span> "eyJhbGciOiJIUzUxMiJ<span class="token number">9.</span>eyJqdGkiOiI<span class="token number">0</span>MzI<span class="token number">5</span>Iiwic<span class="token number">3</span>ViIjoiZHMyNDI<span class="token number">0</span>IiwiaXN
          zIjoiQUJDX<span class="token number">0</span>x<span class="token number">0</span>ZCIsImF<span class="token number">1</span>ZCI<span class="token number">6</span>IlhZWl<span class="token number">9</span>MdGQiLCJpYXQiOjE<span class="token number">2</span>MDc<span class="token number">0</span>MzA<span class="token number">5</span>
          OTIsImV<span class="token number">4</span>cCI<span class="token number">6</span>MTYwNzQzNDU<span class="token number">5</span>Mn<span class="token number">0.</span>hIET_EjL<span class="token number">6</span>dqgdUMX-dH<span class="token number">9</span>a<span class="token number">7</span>msPHSO<span class="token number">5</span>-
          GlLFfSotXWWvvxO<span class="token number">69</span>hVOLjkiUGYKBZDyux<span class="token number">0</span>QRA_bb<span class="token number">75</span>Mpp<span class="token number">34</span>EOXLHYiw",
<span class="token string">"message"</span><span class="token punctuation">:</span> <span class="token string">"Token generated successfully!"</span>
<span class="token punctuation">}</span><span class="line-numbers-rows"><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre> </div>

<p>♠ if entered wrong username/password then output will be as below :</p>

<div class="code-embed-wrapper"> <div class="code-embed-infos"> <span class="code-embed-name">Bad Output</span> </div> <pre class=" code-embed-pre line-numbers language-css" data-start="1" data-line-offset="0" style="counter-reset: linenumber 0;"><code class=" code-embed-code language-css"><span class="token punctuation">{</span>
<span class="token string">"timestamp"</span><span class="token punctuation">:</span> <span class="token string">"2020-12-08T12:38:25.778+00:00"</span>,
<span class="token string">"status"</span><span class="token punctuation">:</span> <span class="token number">401</span>,
<span class="token string">"error"</span><span class="token punctuation">:</span> <span class="token string">"Unauthorized"</span>,
<span class="token string">"trace"</span><span class="token punctuation">:</span> "org<span class="token number">.</span>springframework<span class="token number">.</span>security<span class="token number">.</span>authentication<span class="token number">.</span><span class="token property">BadCredentialsException</span><span class="token punctuation">:</span> Bad credentials\r\n\tat org<span class="token number">.....................................</span>
<span class="token string">"message"</span><span class="token punctuation">:</span> <span class="token string">"UnAuthorized User"</span>,
<span class="token string">"path"</span><span class="token punctuation">:</span> <span class="token string">"/user/loginUser"</span>
<span class="token punctuation">}</span><span class="line-numbers-rows"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre> </div>

<h3><span id="3_Access_dataresource_within_token_validity_period"><span style="color: #000080;">3) Access data/resource within token validity period</span></span></h3>

<p>Enter URL <span style="background-color: #ccffff;">http://localhost:8080/user/getData</span> in Postman URL bar, select POST method, then Select Headers. Under Headers select key as ‘Authorization’. Now paste token as a value of Authorization as in below screenshot. Then click on ‘Send’ button.</p>

<p><img class="aligncenter wp-image-2129 size-full lazyloaded" src="https://i0.wp.com/javatechonline.com/wp-content/uploads/2020/12/JWT1-2.jpg?resize=640%2C318&amp;ssl=1" alt="How To Implement JWT Authentication In Spring Boot Project?" width="640" height="318" data-recalc-dims="1" sizes="(max-width: 640px) 100vw, 640px" srcset="https://i0.wp.com/javatechonline.com/wp-content/uploads/2020/12/JWT1-2.jpg?w=1100&amp;ssl=1 1100w, https://i0.wp.com/javatechonline.com/wp-content/uploads/2020/12/JWT1-2.jpg?resize=300%2C149&amp;ssl=1 300w, https://i0.wp.com/javatechonline.com/wp-content/uploads/2020/12/JWT1-2.jpg?resize=1024%2C509&amp;ssl=1 1024w, https://i0.wp.com/javatechonline.com/wp-content/uploads/2020/12/JWT1-2.jpg?resize=768%2C382&amp;ssl=1 768w, https://i0.wp.com/javatechonline.com/wp-content/uploads/2020/12/JWT1-2.jpg?resize=600%2C298&amp;ssl=1 600w" data-ll-status="loaded"><noscript></p>

<p>As a successful response, you should get the below output :</p>
<p>♠ if entered wrong username/password then output will be as below :</p>

<div class="code-embed-wrapper"> <div class="code-embed-infos"> <span class="code-embed-name">Bad Output</span> </div> <pre class=" code-embed-pre line-numbers language-css" data-start="1" data-line-offset="0" style="counter-reset: linenumber 0;"><code class=" code-embed-code language-css"><span class="token punctuation">{</span>
<span class="token string">"timestamp"</span><span class="token punctuation">:</span> <span class="token string">"2020-12-08T12:38:25.778+00:00"</span>,
<span class="token string">"status"</span><span class="token punctuation">:</span> <span class="token number">401</span>,
<span class="token string">"error"</span><span class="token punctuation">:</span> <span class="token string">"Unauthorized"</span>,
<span class="token string">"trace"</span><span class="token punctuation">:</span> "org<span class="token number">.</span>springframework<span class="token number">.</span>security<span class="token number">.</span>authentication<span class="token number">.</span><span class="token property">BadCredentialsException</span><span class="token punctuation">:</span> Bad credentials\r\n\tat org<span class="token number">.....................................</span>
<span class="token string">"message"</span><span class="token punctuation">:</span> <span class="token string">"UnAuthorized User"</span>,
<span class="token string">"path"</span><span class="token punctuation">:</span> <span class="token string">"/user/loginUser"</span>
<span class="token punctuation">}</span><span class="line-numbers-rows"><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span></span></code></pre> </div>

<h3><span id="3_Access_dataresource_within_token_validity_period"><span style="color: #000080;">3) Access data/resource within token validity period</span></span></h3>

<p>Enter URL <span style="background-color: #ccffff;">http://localhost:8080/user/getData</span> in Postman URL bar, select POST method, then Select Headers. Under Headers select key as ‘Authorization’. Now paste token as a value of Authorization as in below screenshot. Then click on ‘Send’ button.</p>

<p><img class="aligncenter wp-image-2129 size-full lazyloaded" src="https://i0.wp.com/javatechonline.com/wp-content/uploads/2020/12/JWT1-2.jpg?resize=640%2C318&amp;ssl=1" alt="How To Implement JWT Authentication In Spring Boot Project?" width="640" height="318" data-recalc-dims="1" sizes="(max-width: 640px) 100vw, 640px" srcset="https://i0.wp.com/javatechonline.com/wp-content/uploads/2020/12/JWT1-2.jpg?w=1100&amp;ssl=1 1100w, https://i0.wp.com/javatechonline.com/wp-content/uploads/2020/12/JWT1-2.jpg?resize=300%2C149&amp;ssl=1 300w, https://i0.wp.com/javatechonline.com/wp-content/uploads/2020/12/JWT1-2.jpg?resize=1024%2C509&amp;ssl=1 1024w, https://i0.wp.com/javatechonline.com/wp-content/uploads/2020/12/JWT1-2.jpg?resize=768%2C382&amp;ssl=1 768w, https://i0.wp.com/javatechonline.com/wp-content/uploads/2020/12/JWT1-2.jpg?resize=600%2C298&amp;ssl=1 600w" data-ll-status="loaded"><noscript></p>

<p>As a successful response, you should get the below output :</p>

<p>You are accessing data after a valid Login. You are :ds2525</p>
