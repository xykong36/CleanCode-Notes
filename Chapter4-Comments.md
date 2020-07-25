* Good Comments

  * Legal Comments
  
  作用: 法务及知识产权相关 
  ```
  // Copyright (C) 2003,2004,2005 by Object Mentor, Inc. All rights reserved.
  // Released under the terms of the GNU General Public License version 2 or later.
  ```

  * Informative Comments:
  
  作用: 提供有价值的背景信息以及总结
  ```java
  // Returns an instance of the Responder being tested.
  protected abstract Responder responderInstance();
  
  // format matched kk:mm:ss EEE, MMM dd, yyyy
  Pattern timeMatcher = Pattern.compile("\\d*:\\d*:\\d* \\w*, \\w* \\d*, \\d*");
  ```
 
  * Explanation of Intent
  
  作用: 解释代码的意图
  ```java
  public void testConcurrentAddWidgets() throws Exception {
    WidgetBuilder widgetBuilder =
            new WidgetBuilder(new Class[]{BoldWidget.class});
    String text = "’’’bold text’’’";
    ParentWidget parent =
            new BoldWidget(new MockWidgetRoot(), "’’’bold text’’’");
    AtomicBoolean failFlag = new AtomicBoolean();
    failFlag.set(false);

    //This is our best attempt to get a race condition
    //by creating large number of threads.
    for (int i = 0; i < 25000; i++) {
        WidgetBuilderThread widgetBuilderThread =
                new WidgetBuilderThread(widgetBuilder, text, parent, failFlag);
        Thread thread = new Thread(widgetBuilderThread);
        thread.start();
    }
    assertEquals(false, failFlag.get());
  }
  ```
  
  * Clarification
  
  作用: 辅助解释代码的作用
  ```java
  assertTrue(a.compareTo(a) == 0);    // a == a
  assertTrue(a.compareTo(b) != 0);    // a != b
  ```

  * TODO
  
  作用: 进行标记，可以用于任务分配以及合作
  ```java
  //TODO-MdM these are not needed
  // We expect this to go away when we do the checkout model
  protected VersionInfo makeVersion() throws Exception {
      return null;
  }
  ```
  
  
* Bad Comments

  * Mumbling / Noisy / Redundant Comments
  
  问题: 注释的内容 都是一些没有实际意义的废话
  ```java
  /**
   * The container event listeners for this Container.
   */
  protected ArrayList listeners = new ArrayList();
  /**
   * The day of the month.
   */
  private int dayOfMonth;

  ```
  
  * Misleading Comments
  
  问题: 这个例子中的代码并没有在 this.closed 为true的时候直接返回, 当this.closed变为true的时候还在等待
  ```java
  // Utility method that returns when this.closed is true. Throws an exception
  // if the timeout is reached.
  public synchronized void waitForClose(final long timeoutMillis)
          throws Exception {
      if (!closed) {
          wait(timeoutMillis);
          if (!closed)
              throw new Exception("MockResponseSender could not be closed");
      }
  }
  ```
  
  * Mandated Comments  
  
  问题: 注释中记录的param少了两个变量 并且名字不一致
  ```java
    /**
   * @param title             The title of the CD
   * @param author            The author of the CD
   * @param tracks            The number of tracks on the CD
   * @param durationInMinutes The duration of the CD in minutes
   */
  public void addCD(String title, String author,
                    int tracks, int durationInMinutes) {
      CD cd = new CD();
      cd.title = title;
      cd.author = author;
      cd.tracks = tracks;
      cd.duration = duration;
      cdList.add(cd);
  }
  ```

  * Commented-Out Code
  
  问题: 应该删除的代码没有删除
  ```java
  InputStreamResponse response = new InputStreamResponse();
  response.setBody(formatter.getResultStream(), formatter.getByteCount());
  // InputStream resultsStream = formatter.getResultStream();
  // StreamReader reader = new StreamReader(resultsStream);
  // response.setContent(reader.read(formatter.getByteCount()));
  ```
  
  * Inobvious Connection
  
  问题: 注释描述的内容和当前function中的变量对应关系不明确，造成歧义，无法直接进行修改
  ```java
  /*
   * start with an array that is big enough to hold all the pixels
   * (plus filter bytes), and an extra 200 bytes for header info
   */
  this.pngBytes = new byte[((this.width + 1) * this.height * 3) + 200];
  ```
  
  * Nonlocal Information
  
  问题: 注释中的内容不是在当前function使用的，即使描述的信息是准确的也没有任何帮助
  ```java
  /**
   * Port on which fitnesse would run. Defaults to 8082.
   *
   * @param fitnessePort
   */
  public void setFitnessePort(int fitnessePort) {
      this.fitnessePort = fitnessePort;
  }
  ```
  
