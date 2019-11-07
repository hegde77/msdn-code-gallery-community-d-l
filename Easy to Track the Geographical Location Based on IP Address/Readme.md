# Easy to Track the Geographical Location Based on IP Address.
## Requires
- Visual Studio 2008
## License
- Apache License, Version 2.0
## Technologies
- ASP.NET
- Visual Studio Extensions
- .NET 3.0
- .NET Framework 4.0
## Topics
- Security
- IP Address
- WebBrowser
- HttpWebRequest
## Updated
- 04/28/2011
## Description

<h2>Table of Contents</h2>
<p style="text-align:left"><span style="font-size:small"><em>* Introduction<br>
* Quick Overview<br>
* How to Achieve<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;o How to Use the Services<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;o Get the User IP<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; o Get the User Location</em></span></p>
<p style="text-align:left"><span style="font-size:small"><em>&nbsp;* Conclusion<br>
&nbsp;* References<br>
&nbsp;* History</em></span></p>
<h1>Introduction</h1>
<p>Developers are very much familiar with the use of IP tracking system, Microsoft Visual Studio .NET provides a number of class, methods to do this. This article is not about getting the user IP only, but also finds the geographical location of a user who
 is browsing your ASP.NET application. For example, you have an ASP.NET application, your hosting is done, your web address is suppose &rdquo;www.xyz.com&rdquo;, now you want to track / maintain a log of the visitors IP with the location something like:</p>
<p>IP: XXX.XXX.XXX.XXX, TIMESTAMP: 3/2/2010 4:18:39 PM, COUNTRY= BANGLADESH, <br>
COUNTRY CODE= BD, CITY= DHAKA, etc.</p>
<p>Sample output figure:</p>
<p><img src="21427-info.png" alt="" width="550" height="245"></p>
<h1>Quick Overview</h1>
<p>Before we start, we need to know some basic knowledge, on System.Net, System.Data namespace provide by Microsoft Visual Studio .Net, HTTP Server variables.</p>
<p>More information can be found at<a href="http://msdn.microsoft.com/en-us/library/system.net.aspx" target="_blank"> this link</a>.</p>
<h1>How to Achieve</h1>
<p>If you search for the solution on the internet; you may get many ways to do it. For example, you can use web service or download database containing the location mapped with the IP, but most of them are not free to use / allow you to a very limited number
 of hits per day&hellip; I found some sites that allow you free access for getting the user location from IP, some of the site(s) are listed below:</p>
<p>&nbsp;&nbsp;&nbsp; * <a href="http://freegeoip.appspot.com">http://freegeoip.appspot.com</a><br>
&nbsp;&nbsp;&nbsp; * <a href="http://ws.cdyne.com/">http://ws.cdyne.com/</a><br>
&nbsp;&nbsp;&nbsp; * <a href="http://ipinfodb.com/">http://ipinfodb.com/</a></p>
<p>Note: All the above listed addresses reply in standard XML format.</p>
<h2>How to Use the Services</h2>
<p>In this section, I would like to discuss how to use the site(s) to retrieve a user geographical location. You can choose any one of them, before that you need to know what are the parameters required, let's start one by one:<br>
(i)http://freegeoip.appspot.com</p>
<p>Parameter: IP Address (xxx.xxx.xxx.xxx).<br>
URL sample: <a href="http://freegeoip.appspot.com/xml/xxx.xxx.xxx.xxx">http://freegeoip.appspot.com/xml/xxx.xxx.xxx.xxx</a><br>
Output: Standard XML</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>XML</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span></div>
<span class="hidden">xml</span>
<pre class="hidden">&lt;?xml version=&quot;1.0&quot; encoding=&quot;UTF-8&quot;?&gt;
&lt;Response&gt;
    &lt;Status&gt;true&lt;/Status&gt;
    &lt;Ip&gt;xxx.xxx.xxx.xxx&lt;/Ip&gt;
    &lt;CountryCode&gt;BD&lt;/CountryCode&gt;
    &lt;CountryName&gt;Bangladesh&lt;/CountryName&gt;
    &lt;RegionCode&gt;81&lt;/RegionCode&gt;
    &lt;RegionName&gt;Dhaka&lt;/RegionName&gt;
    &lt;City&gt;Dhaka&lt;/City&gt;
    &lt;ZipCode&gt;&lt;/ZipCode&gt;
    &lt;Latitude&gt;23.723&lt;/Latitude&gt;
    &lt;Longitude&gt;90.4086&lt;/Longitude&gt;
&lt;/Response&gt;

</pre>
<div class="preview">
<pre class="xml"><span class="xml__tag_start">&lt;?xml</span>&nbsp;<span class="xml__attr_name">version</span>=<span class="xml__attr_value">&quot;1.0&quot;</span>&nbsp;<span class="xml__attr_name">encoding</span>=<span class="xml__attr_value">&quot;UTF-8&quot;</span><span class="xml__tag_start">?&gt;</span>&nbsp;
<span class="xml__tag_start">&lt;Response</span><span class="xml__tag_start">&gt;&nbsp;
</span>&nbsp;&nbsp;&nbsp;&nbsp;<span class="xml__tag_start">&lt;Status</span><span class="xml__tag_start">&gt;</span>true<span class="xml__tag_end">&lt;/Status&gt;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="xml__tag_start">&lt;Ip</span><span class="xml__tag_start">&gt;</span>xxx.xxx.xxx.xxx<span class="xml__tag_end">&lt;/Ip&gt;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="xml__tag_start">&lt;CountryCode</span><span class="xml__tag_start">&gt;</span>BD<span class="xml__tag_end">&lt;/CountryCode&gt;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="xml__tag_start">&lt;CountryName</span><span class="xml__tag_start">&gt;</span>Bangladesh<span class="xml__tag_end">&lt;/CountryName&gt;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="xml__tag_start">&lt;RegionCode</span><span class="xml__tag_start">&gt;</span>81<span class="xml__tag_end">&lt;/RegionCode&gt;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="xml__tag_start">&lt;RegionName</span><span class="xml__tag_start">&gt;</span>Dhaka<span class="xml__tag_end">&lt;/RegionName&gt;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="xml__tag_start">&lt;City</span><span class="xml__tag_start">&gt;</span>Dhaka<span class="xml__tag_end">&lt;/City&gt;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="xml__tag_start">&lt;ZipCode</span><span class="xml__tag_start">&gt;</span><span class="xml__tag_end">&lt;/ZipCode&gt;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="xml__tag_start">&lt;Latitude</span><span class="xml__tag_start">&gt;</span>23.723<span class="xml__tag_end">&lt;/Latitude&gt;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;<span class="xml__tag_start">&lt;Longitude</span><span class="xml__tag_start">&gt;</span>90.4086<span class="xml__tag_end">&lt;/Longitude&gt;</span>&nbsp;
<span class="xml__tag_end">&lt;/Response&gt;</span>&nbsp;
&nbsp;
&nbsp;
&nbsp;
</pre>
</div>
</div>
</div>
<div class="endscriptcode">&nbsp;</div>
<div class="endscriptcode">
<p>(ii)http://ws.cdyne.com/</p>
<p>&nbsp;&nbsp;&nbsp; * Parameter: IP Address (xxx.xxx.xxx.xxx) &amp; License Key<br>
&nbsp;&nbsp;&nbsp; * URL sample: <a href="http://ws.cdyne.com/ip2geo/ip2geo.asmx/ResolveIP?ipAddress=xxx.xxx.xxx.xxx&licenseKey=0">
http://ws.cdyne.com/ip2geo/ip2geo.asmx/ResolveIP?ipAddress=xxx.xxx.xxx.xxx&amp;licenseKey=0</a><br>
&nbsp;&nbsp;&nbsp; * Output: Standard XML</p>
<p>Output: Standard XML</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>XML</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span></div>
<span class="hidden">xml</span>
<pre class="hidden">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;
&lt;IPInformation xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance 
 xmlns:xsd=&quot;http://www.w3.org/2001/XMLSchema&quot; xmlns=&quot;http://ws.cdyne.com/&quot;&gt;
  &lt;City&gt;Dhaka&lt;/City&gt;
  &lt;StateProvince&gt;81&lt;/StateProvince&gt;
  &lt;Country&gt;Bangladesh&lt;/Country&gt;
  &lt;Organization /&gt;
  &lt;Latitude&gt;23.72301&lt;/Latitude&gt;
  &lt;Longitude&gt;90.4086&lt;/Longitude&gt;
  &lt;AreaCode&gt;0&lt;/AreaCode&gt;
  &lt;TimeZone /&gt;
  &lt;HasDaylightSavings&gt;false&lt;/HasDaylightSavings&gt;
  &lt;Certainty&gt;90&lt;/Certainty&gt;
  &lt;RegionName /&gt;
  &lt;CountryCode&gt;BD&lt;/CountryCode&gt;
&lt;/IPInformation&gt;

</pre>
<div class="preview">
<pre class="xml"><span class="xml__tag_start">&lt;?xml</span>&nbsp;<span class="xml__attr_name">version</span>=<span class="xml__attr_value">&quot;1.0&quot;</span>&nbsp;<span class="xml__attr_name">encoding</span>=<span class="xml__attr_value">&quot;utf-8&quot;</span><span class="xml__tag_start">?&gt;</span>&nbsp;
<span class="xml__tag_start">&lt;IPInformation</span>&nbsp;<span class="xml__keyword">xmlns</span>:xsi=http://www.w3.org/2001/XMLSchema-instance&nbsp;&nbsp;
&nbsp;<span class="xml__keyword">xmlns</span>:<span class="xml__attr_name">xsd</span>=<span class="xml__attr_value">&quot;http://www.w3.org/2001/XMLSchema&quot;</span>&nbsp;<span class="xml__attr_name">xmlns</span>=<span class="xml__attr_value">&quot;http://ws.cdyne.com/&quot;</span><span class="xml__tag_start">&gt;&nbsp;
</span>&nbsp;&nbsp;<span class="xml__tag_start">&lt;City</span><span class="xml__tag_start">&gt;</span>Dhaka<span class="xml__tag_end">&lt;/City&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;StateProvince</span><span class="xml__tag_start">&gt;</span>81<span class="xml__tag_end">&lt;/StateProvince&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;Country</span><span class="xml__tag_start">&gt;</span>Bangladesh<span class="xml__tag_end">&lt;/Country&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;Organization</span>&nbsp;<span class="xml__tag_start">/&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;Latitude</span><span class="xml__tag_start">&gt;</span>23.72301<span class="xml__tag_end">&lt;/Latitude&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;Longitude</span><span class="xml__tag_start">&gt;</span>90.4086<span class="xml__tag_end">&lt;/Longitude&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;AreaCode</span><span class="xml__tag_start">&gt;</span>0<span class="xml__tag_end">&lt;/AreaCode&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;TimeZone</span>&nbsp;<span class="xml__tag_start">/&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;HasDaylightSavings</span><span class="xml__tag_start">&gt;</span>false<span class="xml__tag_end">&lt;/HasDaylightSavings&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;Certainty</span><span class="xml__tag_start">&gt;</span>90<span class="xml__tag_end">&lt;/Certainty&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;RegionName</span>&nbsp;<span class="xml__tag_start">/&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;CountryCode</span><span class="xml__tag_start">&gt;</span>BD<span class="xml__tag_end">&lt;/CountryCode&gt;</span>&nbsp;
<span class="xml__tag_end">&lt;/IPInformation&gt;</span>&nbsp;
&nbsp;
&nbsp;
&nbsp;
</pre>
</div>
</div>
</div>
<div class="endscriptcode">&nbsp;</div>
<p>Blocks of code should be set as style &quot;Formatted&quot; like this:<br>
(iii)http://ipinfodb.com/</p>
<p>&nbsp;&nbsp;&nbsp; * Parameter: IP Address (xxx.xxx.xxx.xxx)<br>
&nbsp;&nbsp;&nbsp; * URL sample:http://ipinfodb.com/ip_query.php?ip=xxx.xxx.xxx.xxx0<br>
&nbsp;&nbsp;&nbsp; * Output: Standard XML</p>
<p>Output: Standard XML</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>XML</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span></div>
<span class="hidden">xml</span>
<pre class="hidden">&lt;?xml version=&quot;1.0&quot; encoding=&quot;UTF-8&quot;?&gt;
&lt;Response&gt;
  &lt;Ip&gt;xxx.xxx.xxx.xxx&lt;/Ip&gt;
  &lt;Status&gt;OK&lt;/Status&gt;
  &lt;CountryCode&gt;BD&lt;/CountryCode&gt;
  &lt;CountryName&gt;Bangladesh&lt;/CountryName&gt;
  &lt;RegionCode&gt;81&lt;/RegionCode&gt;
  &lt;RegionName&gt;Dhaka&lt;/RegionName&gt;
  &lt;City&gt;Dhaka&lt;/City&gt;
  &lt;ZipPostalCode&gt;&lt;/ZipPostalCode&gt;
  &lt;Latitude&gt;23.7231&lt;/Latitude&gt;
  &lt;Longitude&gt;90.4086&lt;/Longitude&gt;
  &lt;Timezone&gt;6&lt;/Timezone&gt;
  &lt;Gmtoffset&gt;6&lt;/Gmtoffset&gt;
  &lt;Dstoffset&gt;6&lt;/Dstoffset&gt;
&lt;/Response&gt;


</pre>
<div class="preview">
<pre class="xml"><span class="xml__tag_start">&lt;?xml</span>&nbsp;<span class="xml__attr_name">version</span>=<span class="xml__attr_value">&quot;1.0&quot;</span>&nbsp;<span class="xml__attr_name">encoding</span>=<span class="xml__attr_value">&quot;UTF-8&quot;</span><span class="xml__tag_start">?&gt;</span>&nbsp;
<span class="xml__tag_start">&lt;Response</span><span class="xml__tag_start">&gt;&nbsp;
</span>&nbsp;&nbsp;<span class="xml__tag_start">&lt;Ip</span><span class="xml__tag_start">&gt;</span>xxx.xxx.xxx.xxx<span class="xml__tag_end">&lt;/Ip&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;Status</span><span class="xml__tag_start">&gt;</span>OK<span class="xml__tag_end">&lt;/Status&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;CountryCode</span><span class="xml__tag_start">&gt;</span>BD<span class="xml__tag_end">&lt;/CountryCode&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;CountryName</span><span class="xml__tag_start">&gt;</span>Bangladesh<span class="xml__tag_end">&lt;/CountryName&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;RegionCode</span><span class="xml__tag_start">&gt;</span>81<span class="xml__tag_end">&lt;/RegionCode&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;RegionName</span><span class="xml__tag_start">&gt;</span>Dhaka<span class="xml__tag_end">&lt;/RegionName&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;City</span><span class="xml__tag_start">&gt;</span>Dhaka<span class="xml__tag_end">&lt;/City&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;ZipPostalCode</span><span class="xml__tag_start">&gt;</span><span class="xml__tag_end">&lt;/ZipPostalCode&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;Latitude</span><span class="xml__tag_start">&gt;</span>23.7231<span class="xml__tag_end">&lt;/Latitude&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;Longitude</span><span class="xml__tag_start">&gt;</span>90.4086<span class="xml__tag_end">&lt;/Longitude&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;Timezone</span><span class="xml__tag_start">&gt;</span>6<span class="xml__tag_end">&lt;/Timezone&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;Gmtoffset</span><span class="xml__tag_start">&gt;</span>6<span class="xml__tag_end">&lt;/Gmtoffset&gt;</span>&nbsp;
&nbsp;&nbsp;<span class="xml__tag_start">&lt;Dstoffset</span><span class="xml__tag_start">&gt;</span>6<span class="xml__tag_end">&lt;/Dstoffset&gt;</span>&nbsp;
<span class="xml__tag_end">&lt;/Response&gt;</span>&nbsp;
&nbsp;
&nbsp;
&nbsp;
&nbsp;
</pre>
</div>
</div>
</div>
<div class="endscriptcode">&nbsp;</div>
<h2>Get the User IP</h2>
<p>I use a very common technique. Actually this is nothing but the using of HTTP server variables. The following server variables are used for this purpose.</p>
<p>&nbsp;&nbsp;&nbsp; * HTTP_X_FORWARDED_FOR<br>
&nbsp;&nbsp;&nbsp; * REMOTE_ADDR</p>
<p>A sample code snippet is given below:</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>C#</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span></div>
<span class="hidden">csharp</span>
<pre class="hidden">private string GetVisitor()
    {        
        string strIPAddress = string.Empty;
        string strVisitorCountry = string.Empty;

        strIPAddress = Request.ServerVariables[&quot;HTTP_X_FORWARDED_FOR&quot;];

        if (strIPAddress == &quot;&quot; || strIPAddress == null)
            strIPAddress = Request.ServerVariables[&quot;REMOTE_ADDR&quot;];

        Tools.GetLocation.IVisitorsGeographicalLocation _objLocation;
        _objLocation = new Tools.GetLocation.ClsVisitorsGeographicalLocation();

        DataTable _objDataTable = _objLocation.GetLocation(strIPAddress);

        if (_objDataTable != null)
        {
            if (_objDataTable.Rows.Count &gt; 0)
            {
                strVisitorCountry = 
                            &quot;IP: &quot;
                            &#43; strIPAddress
                            &#43; &quot;, TIMESTAMP: &quot; 
                            &#43; Convert.ToString(System.DateTime.Now)     
                            &#43; &quot;, CITY: &quot;
                            &#43; Convert.ToString(_objDataTable.Rows[0][&quot;City&quot;]).ToUpper()
                            &#43; &quot;, COUNTRY: &quot;
                            &#43; Convert.ToString(_objDataTable.Rows[0]
     [&quot;CountryName&quot;]).ToUpper()
                            &#43; &quot;, COUNTRY CODE: &quot;
                            &#43; Convert.ToString(_objDataTable.Rows[0]
     [&quot;CountryCode&quot;]).ToUpper();
            }
            else
            {
                strVisitorCountry = null;
            }
        }
        return strVisitorCountry;
    }


</pre>
<div class="preview">
<pre class="csharp"><span class="cs__keyword">private</span>&nbsp;<span class="cs__keyword">string</span>&nbsp;GetVisitor()&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__keyword">string</span>&nbsp;strIPAddress&nbsp;=&nbsp;<span class="cs__keyword">string</span>.Empty;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__keyword">string</span>&nbsp;strVisitorCountry&nbsp;=&nbsp;<span class="cs__keyword">string</span>.Empty;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strIPAddress&nbsp;=&nbsp;Request.ServerVariables[<span class="cs__string">&quot;HTTP_X_FORWARDED_FOR&quot;</span>];&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__keyword">if</span>&nbsp;(strIPAddress&nbsp;==&nbsp;<span class="cs__string">&quot;&quot;</span>&nbsp;||&nbsp;strIPAddress&nbsp;==&nbsp;<span class="cs__keyword">null</span>)&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strIPAddress&nbsp;=&nbsp;Request.ServerVariables[<span class="cs__string">&quot;REMOTE_ADDR&quot;</span>];&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Tools.GetLocation.IVisitorsGeographicalLocation&nbsp;_objLocation;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;_objLocation&nbsp;=&nbsp;<span class="cs__keyword">new</span>&nbsp;Tools.GetLocation.ClsVisitorsGeographicalLocation();&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DataTable&nbsp;_objDataTable&nbsp;=&nbsp;_objLocation.GetLocation(strIPAddress);&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__keyword">if</span>&nbsp;(_objDataTable&nbsp;!=&nbsp;<span class="cs__keyword">null</span>)&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__keyword">if</span>&nbsp;(_objDataTable.Rows.Count&nbsp;&gt;&nbsp;<span class="cs__number">0</span>)&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strVisitorCountry&nbsp;=&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__string">&quot;IP:&nbsp;&quot;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#43;&nbsp;strIPAddress&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#43;&nbsp;<span class="cs__string">&quot;,&nbsp;TIMESTAMP:&nbsp;&quot;</span>&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#43;&nbsp;Convert.ToString(System.DateTime.Now)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#43;&nbsp;<span class="cs__string">&quot;,&nbsp;CITY:&nbsp;&quot;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#43;&nbsp;Convert.ToString(_objDataTable.Rows[<span class="cs__number">0</span>][<span class="cs__string">&quot;City&quot;</span>]).ToUpper()&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#43;&nbsp;<span class="cs__string">&quot;,&nbsp;COUNTRY:&nbsp;&quot;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#43;&nbsp;Convert.ToString(_objDataTable.Rows[<span class="cs__number">0</span>]&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[<span class="cs__string">&quot;CountryName&quot;</span>]).ToUpper()&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#43;&nbsp;<span class="cs__string">&quot;,&nbsp;COUNTRY&nbsp;CODE:&nbsp;&quot;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#43;&nbsp;Convert.ToString(_objDataTable.Rows[<span class="cs__number">0</span>]&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[<span class="cs__string">&quot;CountryCode&quot;</span>]).ToUpper();&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__keyword">else</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;strVisitorCountry&nbsp;=&nbsp;<span class="cs__keyword">null</span>;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__keyword">return</span>&nbsp;strVisitorCountry;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;}&nbsp;
&nbsp;
&nbsp;
&nbsp;
&nbsp;
</pre>
</div>
</div>
</div>
<div class="endscriptcode">&nbsp;</div>
<h2>Get the User Location</h2>
<p>To get the location, you just need to use the following provided by Microsoft Visual Studio .NET:</p>
<p>&nbsp;&nbsp;&nbsp; * WebRequest<br>
&nbsp;&nbsp;&nbsp; * WebResponse<br>
&nbsp;&nbsp;&nbsp; * WebProxy</p>
<p>More information can be found at<a href="http://msdn.microsoft.com/en-us/library/system.net.webrequest.aspx" target="_blank"> this link</a>.</p>
<p>A sample code snippet is given below:</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>C#</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span></div>
<span class="hidden">csharp</span>
<pre class="hidden">public DataTable GetLocation(string strIPAddress)
        {
            //Create a WebRequest with the current Ip
            WebRequest _objWebRequest =
                WebRequest.Create(http://freegeoip.appspot.com/xml/ 
  //http://ipinfodb.com/ip_query.php?ip=
                               &#43; strIPAddress);
            //Create a Web Proxy
            WebProxy _objWebProxy =
               new WebProxy(&quot;http://freegeoip.appspot.com/xml/&quot;
                         &#43; strIPAddress, true);

            //Assign the proxy to the WebRequest
            _objWebRequest.Proxy = _objWebProxy;

            //Set the timeout in Seconds for the WebRequest
            _objWebRequest.Timeout = 2000;

            try
            {
                //Get the WebResponse 
                WebResponse _objWebResponse = _objWebRequest.GetResponse();
                //Read the Response in a XMLTextReader
                XmlTextReader _objXmlTextReader
                    = new XmlTextReader(_objWebResponse.GetResponseStream());

                //Create a new DataSet
                DataSet _objDataSet = new DataSet();
                //Read the Response into the DataSet
                _objDataSet.ReadXml(_objXmlTextReader);

                return _objDataSet.Tables[0];
            }
            catch
            {
                return null;
            }
        } // End of GetLocation  


</pre>
<div class="preview">
<pre class="csharp"><span class="cs__keyword">public</span>&nbsp;DataTable&nbsp;GetLocation(<span class="cs__keyword">string</span>&nbsp;strIPAddress)&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__com">//Create&nbsp;a&nbsp;WebRequest&nbsp;with&nbsp;the&nbsp;current&nbsp;Ip</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WebRequest&nbsp;_objWebRequest&nbsp;=&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WebRequest.Create(http:<span class="cs__com">//freegeoip.appspot.com/xml/&nbsp;</span>&nbsp;
&nbsp;&nbsp;<span class="cs__com">//http://ipinfodb.com/ip_query.php?ip=</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#43;&nbsp;strIPAddress);&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__com">//Create&nbsp;a&nbsp;Web&nbsp;Proxy</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WebProxy&nbsp;_objWebProxy&nbsp;=&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__keyword">new</span>&nbsp;WebProxy(<span class="cs__string">&quot;http://freegeoip.appspot.com/xml/&quot;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#43;&nbsp;strIPAddress,&nbsp;<span class="cs__keyword">true</span>);&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__com">//Assign&nbsp;the&nbsp;proxy&nbsp;to&nbsp;the&nbsp;WebRequest</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;_objWebRequest.Proxy&nbsp;=&nbsp;_objWebProxy;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__com">//Set&nbsp;the&nbsp;timeout&nbsp;in&nbsp;Seconds&nbsp;for&nbsp;the&nbsp;WebRequest</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;_objWebRequest.Timeout&nbsp;=&nbsp;<span class="cs__number">2000</span>;&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__keyword">try</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__com">//Get&nbsp;the&nbsp;WebResponse&nbsp;</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WebResponse&nbsp;_objWebResponse&nbsp;=&nbsp;_objWebRequest.GetResponse();&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__com">//Read&nbsp;the&nbsp;Response&nbsp;in&nbsp;a&nbsp;XMLTextReader</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;XmlTextReader&nbsp;_objXmlTextReader&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;=&nbsp;<span class="cs__keyword">new</span>&nbsp;XmlTextReader(_objWebResponse.GetResponseStream());&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__com">//Create&nbsp;a&nbsp;new&nbsp;DataSet</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DataSet&nbsp;_objDataSet&nbsp;=&nbsp;<span class="cs__keyword">new</span>&nbsp;DataSet();&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__com">//Read&nbsp;the&nbsp;Response&nbsp;into&nbsp;the&nbsp;DataSet</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;_objDataSet.ReadXml(_objXmlTextReader);&nbsp;
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__keyword">return</span>&nbsp;_objDataSet.Tables[<span class="cs__number">0</span>];&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__keyword">catch</span>&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="cs__keyword">return</span>&nbsp;<span class="cs__keyword">null</span>;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}&nbsp;<span class="cs__com">//&nbsp;End&nbsp;of&nbsp;GetLocation&nbsp;&nbsp;</span>&nbsp;
&nbsp;
&nbsp;
&nbsp;
&nbsp;
</pre>
</div>
</div>
</div>
<div class="endscriptcode">&nbsp;</div>
<h1>Conclusion</h1>
<p>I hope this might be helpful to you! Enjoy.</p>
<h1><br>
References</h1>
<p>&nbsp;&nbsp;&nbsp; * MSDN</p>
<h1>History</h1>
<p>&nbsp;&nbsp;&nbsp; * 2nd March, 2010: Initial post</p>
</div>
<div class="endscriptcode"></div>