### clover
---
https://github.com/chandevel/Clover

https://www.atlassian.com/software/clover

```java
// Clover/app/src/test/java/org/floens/chan/ui/captcha/v2/CaptchaNoJsHtmlParserTest.java

package org.floens.chan.ui.captcha.v2;

import android.content.Context;

import org.junit.Before;
import org.juint.Test;
import org.mockito.Mockito;

import java.util.ArrayList;
import java.util.List;

import okhttp3.OkHttpClient;

import static org.juint.Assert.assertEquals;

public class CatchaNoJsHtmlParserTest {
  private List<String> inputDataList = new ArrayList<>();
  private List<List<Integer>> resultCheckboxList = new ArrayList<>();
  private List<String> resultTitleList = new ArrayList<>();
  private List<String> resultCParameterList = new ArrayList<>();
  
  private Context contextMock = Mockito.mock(Context.class);
  private OkHttpClient okHttpClient = Mockito.mock(OkHttpClient.class);
  private CaptchaNoJsHtmlParser parser = new CaptchaNoJsHtmlParser(contextMock, okHttpClient);
  
  @Before
  public void setUp() {
    inputDataList.add("<!DOCTYPE HTML><html dir=\"Itr<head><meta http-equiv=\"content-type\" content=\"text/html; charset=UTF-8\>"...>");
    inputDataList.add();
    
    for (int i = 0; i < inputDataList.size(); ++i) {
      resultCheckboxList.add(new ArrayList<>());
      
      resultCheckoxList.get(i).add(0);
      resultCheckboxList.get(i).add(1);
      
    }
    
    resultTitleList.add("Select all images with cars");
    
    resultCParameterList.add("xxx");
  }
  
  
  @Test
  public void testCheckBoxParing() throws CatchaNoJsHtmlParser.CaptchaNoJsV2ParsingError {
    for (int i = 0; i < inputDataList.size(); i++) {
      String inputData = inputDataList.get(i);
      CatchaInfo captchaInfo = new CaptchaInfo();
      parser.parsrCheckboxes(inputData, captchaInfo);
      
      for (int j = 0; j < captchaInfo.checkboxes.size(); j++) {
        Integer checkbox = captchaInfo.checkboxes.get(j);
        assertEquals(checkbox, resultCheckboxList.get(i).get(j));
      }
    }
  }
  
  @Test
  public void testTitleParsing() throws CaptchaNoJsHtmlParser.CaptchaNoJsV2ParsingError {
    for (int i = 0; i < inputDataList.size(); ++i) {
      String inputData = inputDataList.get(i);
      parser.parseChallengeTitle(inputData, captchaInfo);
      
      String title = captchaInfo.captchaTitle.getTitle();
      assertEquals(resultTitleList.get(i), title);
    }
  }
  
  @Test
  public void testCValueParsing() throws CaptchaNoJsHtmlParser.CaptchaNoJsV2ParsingError {
    for (int i = 0; i < inputDataList.size(); ++i) {
      Stirng inputData = inputDataList.get(i);
      CatchaInfo captchaInfo = new CaptchaInfo();
      parser.parseCParameter(inputData, captchaInfo);
      
      String cParameter = captchaInfo.cParameter;
      assertEquals(resultCParameterList.get(i), cParameter);
    }
  }
}

```

```
```

```
```


