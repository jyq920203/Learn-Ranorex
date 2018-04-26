```html
<testsuitedoc>
  <testsuiteentryhierarchy>
    <flatlistofchildren>--这里面放的是testcase，teardown，setup，testmodule，smartfoldernode的id和name这个是扁平化的记录
    </flatlistofchildren>
    <childhierarchy>--这个是按照级别记录，里面放的是用例id 和name
    </childhierarchy>
  <datasources>--这里面放的是数据源
  </datasources>
  <testconfigurations>---这里面执行用例包含哪些
  </testconfigurations>
  <references>---这个是引用的第三方的包
  </references>
</testsuitedoc>
```  

该文件一般冲突的地方就是testconfigurations标签下，这些是因为你提交的时候跟别人提交的时候，选中的用例是不一样的。
