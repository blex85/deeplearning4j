---
title: Deploying Deeplearning4j to Android
layout: default
---

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">        

    <link href="https://maxcdn.bootstrapcdn.com/bootswatch/3.3.7/paper/bootstrap.min.css" rel="stylesheet" integrity="sha384-awusxf8AUojygHf2+joICySzB780jVvQaVCAt1clU3QsyAitLGul28Qxb2r1e5g+" crossorigin="anonymous">
    <link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css" rel="stylesheet" integrity="sha384-T8Gy5hrqNKT+hzMclPo118YTQO6cYprQmhrYwIiQ/3axmI1hQomh7Ud2hPOy8SP1" crossorigin="anonymous">
    <link href="https://fonts.googleapis.com/css?family=Source+Code+Pro" rel="stylesheet">

      <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/SyntaxHighlighter/3.0.83/styles/shCore.min.css">
      <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/SyntaxHighlighter/3.0.83/styles/shThemeEclipse.min.css">
      <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/SyntaxHighlighter/3.0.83/styles/shCoreEclipse.min.css">

    <link href="/css/custom.css" rel="stylesheet">
    <link href="/css/syntax.css" rel="stylesheet">

    <!--[if lt IE 9]>
      <script src="https://oss.maxcdn.com/html5shiv/3.7.3/html5shiv.min.js"></script>
      <script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
    <![endif]-->
    
    <!-- Begin Jekyll SEO tag v2.0.0 -->
<title>How to Use Deeplearning4J in Android Apps - Progur!</title>
<meta property="og:title" content="How to Use Deeplearning4J in Android Apps" />
<meta name="description" content="DeepLearning4J (DL4J) is a very popular Java-based machine learning library that runs on the JVM. In this tutorial, I’ll show you how to use it to create and train neural networks in an Android app." />
<meta property="og:description" content="DeepLearning4J (DL4J) is a very popular Java-based machine learning library that runs on the JVM. In this tutorial, I’ll show you how to use it to create and train neural networks in an Android app." />
<link rel="canonical" href="http://progur.com/2017/01/how-to-use-deeplearning4j-on-android.html" />
<meta property="og:url" content="http://progur.com/2017/01/how-to-use-deeplearning4j-on-android.html" />
<meta property="og:site_name" content="Progur!" />
<meta property="og:type" content="article" />
<meta property="article:published_time" content="2017-01-14T00:00:00+05:30" />
<meta name="twitter:card" content="summary" />
<meta name="twitter:site" content="@hathibel" />
<meta name="twitter:creator" content="@hathibel" />
<script type="application/ld+json">
  {
    "@context": "http://schema.org",
    "@type": "BlogPosting",
    "headline": "How to Use Deeplearning4J in Android Apps",
    "datePublished": "2017-01-14T00:00:00+05:30",
    "description": "DeepLearning4J (DL4J) is a very popular Java-based machine learning library that runs on the JVM. In this tutorial, I’ll show you how to use it to create and train neural networks in an Android app.",
    "logo": "http://progur.com/assets/logo.jpg",
    "url": "http://progur.com/2017/01/how-to-use-deeplearning4j-on-android.html"
  }
</script>
<!-- End Jekyll SEO tag -->
  </head>
  <body>
    <nav class="navbar navbar-default navbar-fixed-top">
      <div class="container">
        <div class="navbar-header">
          <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar" aria-expanded="false" aria-controls="navbar">
            <span class="sr-only">Toggle navigation</span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
          </button>
          <a class="navbar-brand" href="/"><i class="fa fa-terminal logo"></i> PROGUR!</a>
        </div>
        <!-- Options -->
        <div id="navbar" class="collapse navbar-collapse">
          <ul class="nav navbar-nav navbar-right">
            <li><a target="_blank" href="https://twitter.com/hathibel" title="Follow me on Twitter"><i class="fa fa-lg fa-twitter" style="color: #4099FF"></i> &nbsp; Twitter</a></li>
            <li><a target="_blank" href="https://plus.google.com/+Progur" title="Follow me on Google+" ><i class="fa fa-lg fa-google-plus" style="color: #d34836"></i> &nbsp; Google+</a></li>
            <li><a target="_blank" href="https://github.com/hathibelagal" title="Follow me on GitHub"><i class="fa fa-lg fa-github" style="color: #999999"></i> &nbsp; GitHub</a></li>
            <li><a target="_blank" href="https://medium.com/@hathibel" title="Follow me on Medium"><i class="fa fa-lg fa-medium" style="color: #0be370"></i> &nbsp; Medium</a></li>
            <li><a target="_blank" href="/feed.xml" title="Subscribe to our RSS feed"><i class="fa fa-lg fa-rss" style="color: #FF6600"></i>&nbsp; RSS</a></li>
          </ul>
        </div>
        <!-- End of Options -->
      </div>
    </nav>


<div class="container">
    <div class="row">
        <div class="col-md-12">
            <div>
                <div>
                    <h1 class="post-title">How to Use Deeplearning4J in Android Apps</h1>
                    <div class="post-meta">Written by Ashraff Hathibelagal &bull; 14 January 2017</div>
                    <p style="margin-bottom: 20px"><span class="label label-info"><i class="fa fa-tag"> </i> &nbsp; Programming </span></p>
                    <div class="post-actual-content">
                        <p>Usually, training a neural network is a task meant for powerful computers having multiple GPUs. But what if you want to do it on your humble Android phone or tablet? Well, it’s definitely possible. Considering an average Android device’s specifications, however, it will most likely be quite slow. In this quick tutorial, I’ll show you how to use <a href="https://github.com/deeplearning4j/deeplearning4j" target="_blank" rel="nofollow">Deeplearning4J</a>, a popular Java-based deep learning library, to create and train a neural network on an Android device.</p>

<h3 id="prerequisites">Prerequisites</h3>

<p>For best results, you’ll need the following:</p>

<ul>
  <li>An Android device or emulator that runs API level 21 or higher, and has about 200 MB of internal storage space free. I strongly suggest you use an emulator first because you can quickly tweak it in case you run out of memory or storage space.</li>
  <li>Android Studio 2.2 or newer</li>
</ul>

<h3 id="configuring-your-android-studio-project">Configuring Your Android Studio Project</h3>

<p>To be able to use Deeplearning4J in your project, add the following <code class="highlighter-rouge">compile</code> dependencies to your app module’s <strong>build.gradle</strong> file:</p>

<figure class="highlight"><pre><code class="language-groovy" data-lang="groovy"><span class="n">compile</span> <span class="s1">'org.deeplearning4j:deeplearning4j-core:0.7.2'</span>
<span class="n">compile</span> <span class="s1">'org.nd4j:nd4j-native:0.7.2'</span>
<span class="n">compile</span> <span class="s1">'org.nd4j:nd4j-native:0.7.2:android-x86'</span></code></pre></figure>

<p>As you can see, DL4J depends on ND4J, short for N-Dimensions for Java, which is a library that offers fast n-dimensional arrays. ND4J internally depends on a library called JavaCPP, which contains platform-specific native code. Therefore, you must load a version of ND4J that matches the architecture of your Android device. Because I own an x86 device, I’m using <code class="highlighter-rouge">android-x86</code> as the platform.</p>

<p>Dependencies of DL4J and ND4J have several files with identical names. In order to avoid build errors, add the following <code class="highlighter-rouge">exclude</code> parameters to your <code class="highlighter-rouge">packagingOptions</code>.</p>

<figure class="highlight"><pre><code class="language-groovy" data-lang="groovy"><span class="n">packagingOptions</span> <span class="o">{</span>
    <span class="n">exclude</span> <span class="s1">'META-INF/DEPENDENCIES'</span>
    <span class="n">exclude</span> <span class="s1">'META-INF/DEPENDENCIES.txt'</span>
    <span class="n">exclude</span> <span class="s1">'META-INF/LICENSE'</span>
    <span class="n">exclude</span> <span class="s1">'META-INF/LICENSE.txt'</span>
    <span class="n">exclude</span> <span class="s1">'META-INF/license.txt'</span>
    <span class="n">exclude</span> <span class="s1">'META-INF/NOTICE'</span>
    <span class="n">exclude</span> <span class="s1">'META-INF/NOTICE.txt'</span>
    <span class="n">exclude</span> <span class="s1">'META-INF/notice.txt'</span>
    <span class="n">exclude</span> <span class="s1">'META-INF/INDEX.LIST'</span>
<span class="o">}</span></code></pre></figure>

<p>Furthermore, your compiled code will have well over 65,536 methods. To be able to handle this condition, add the following option in the <code class="highlighter-rouge">defaultConfig</code>:</p>

<figure class="highlight"><pre><code class="language-groovy" data-lang="groovy"><span class="n">multiDexEnabled</span> <span class="kc">true</span></code></pre></figure>

<p>And now, press <strong>Sync Now</strong> to update the project.</p>

<h3 id="starting-an-asynchronous-task">Starting an Asynchronous Task</h3>

<p>Training a neural network is CPU-intensive, which is why you wouldn’t want to do it in your application’s UI thread. I’m not too sure if DL4J trains its networks asynchronously by default. Just to be safe, I’ll spawn a separate thread now using the <code class="highlighter-rouge">AsyncTask</code> class.</p>

<figure class="highlight"><pre><code class="language-java" data-lang="java"><span class="n">AsyncTask</span><span class="o">.</span><span class="na">execute</span><span class="o">(</span><span class="k">new</span> <span class="n">Runnable</span><span class="o">()</span> <span class="o">{</span>
    <span class="nd">@Override</span>
    <span class="kd">public</span> <span class="kt">void</span> <span class="nf">run</span><span class="o">()</span> <span class="o">{</span>
        <span class="n">createAndUseNetwork</span><span class="o">();</span>
    <span class="o">}</span>
<span class="o">});</span></code></pre></figure>

<p>Because the method <code class="highlighter-rouge">createAndUseNetwork()</code> doesn’t exist yet, create it.</p>

<figure class="highlight"><pre><code class="language-java" data-lang="java"><span class="kd">private</span> <span class="kt">void</span> <span class="nf">createAndUseNetwork</span><span class="o">()</span> <span class="o">{</span>

<span class="o">}</span></code></pre></figure>

<h3 id="creating-a-neural-network">Creating a Neural Network</h3>

<p>DL4J has a very intuitive API. Let us now use it to create a simple multi-layer perceptron with hidden layers. It will take two input values, and spit out one output value. To create the layers, we’ll use the <code class="highlighter-rouge">DenseLayer</code> and <code class="highlighter-rouge">OutputLayer</code> classes. Accordingly, add the following code to the <code class="highlighter-rouge">createAndUseNetwork()</code> method you created in the previous step.</p>

<figure class="highlight"><pre><code class="language-java" data-lang="java"><span class="n">DenseLayer</span> <span class="n">inputLayer</span> <span class="o">=</span> <span class="k">new</span> <span class="n">DenseLayer</span><span class="o">.</span><span class="na">Builder</span><span class="o">()</span>
        <span class="o">.</span><span class="na">nIn</span><span class="o">(</span><span class="mi">2</span><span class="o">)</span>
        <span class="o">.</span><span class="na">nOut</span><span class="o">(</span><span class="mi">3</span><span class="o">)</span>
        <span class="o">.</span><span class="na">name</span><span class="o">(</span><span class="s">"Input"</span><span class="o">)</span>
        <span class="o">.</span><span class="na">build</span><span class="o">();</span>

<span class="n">DenseLayer</span> <span class="n">hiddenLayer</span> <span class="o">=</span> <span class="k">new</span> <span class="n">DenseLayer</span><span class="o">.</span><span class="na">Builder</span><span class="o">()</span>
        <span class="o">.</span><span class="na">nIn</span><span class="o">(</span><span class="mi">3</span><span class="o">)</span>
        <span class="o">.</span><span class="na">nOut</span><span class="o">(</span><span class="mi">2</span><span class="o">)</span>
        <span class="o">.</span><span class="na">name</span><span class="o">(</span><span class="s">"Hidden"</span><span class="o">)</span>
        <span class="o">.</span><span class="na">build</span><span class="o">();</span>

<span class="n">OutputLayer</span> <span class="n">outputLayer</span> <span class="o">=</span> <span class="k">new</span> <span class="n">OutputLayer</span><span class="o">.</span><span class="na">Builder</span><span class="o">()</span>
        <span class="o">.</span><span class="na">nIn</span><span class="o">(</span><span class="mi">2</span><span class="o">)</span>
        <span class="o">.</span><span class="na">nOut</span><span class="o">(</span><span class="mi">1</span><span class="o">)</span>
        <span class="o">.</span><span class="na">name</span><span class="o">(</span><span class="s">"Output"</span><span class="o">)</span>
        <span class="o">.</span><span class="na">build</span><span class="o">();</span></code></pre></figure>

<p>Now that our layers are ready, let’s create a <code class="highlighter-rouge">NeuralNetConfiguration.Builder</code> object to configure our neural network.</p>

<figure class="highlight"><pre><code class="language-java" data-lang="java"><span class="n">NeuralNetConfiguration</span><span class="o">.</span><span class="na">Builder</span> <span class="n">nncBuilder</span> <span class="o">=</span> <span class="k">new</span> <span class="n">NeuralNetConfiguration</span><span class="o">.</span><span class="na">Builder</span><span class="o">();</span>
<span class="n">nncBuilder</span><span class="o">.</span><span class="na">iterations</span><span class="o">(</span><span class="mi">10000</span><span class="o">);</span>
<span class="n">nncBuilder</span><span class="o">.</span><span class="na">learningRate</span><span class="o">(</span><span class="mf">0.01</span><span class="o">);</span></code></pre></figure>

<p>In the above code, I’ve set the values of two important parameters: learning rate and number of iterations. Feel free to change those values.</p>

<p>We must now create a <code class="highlighter-rouge">NeuralNetConfiguration.ListBuilder</code> object to actually connect our layers and specify their positions.</p>

<figure class="highlight"><pre><code class="language-java" data-lang="java"><span class="n">NeuralNetConfiguration</span><span class="o">.</span><span class="na">ListBuilder</span> <span class="n">listBuilder</span> <span class="o">=</span> <span class="n">nncBuilder</span><span class="o">.</span><span class="na">list</span><span class="o">();</span>
<span class="n">listBuilder</span><span class="o">.</span><span class="na">layer</span><span class="o">(</span><span class="mi">0</span><span class="o">,</span> <span class="n">inputLayer</span><span class="o">);</span>
<span class="n">listBuilder</span><span class="o">.</span><span class="na">layer</span><span class="o">(</span><span class="mi">1</span><span class="o">,</span> <span class="n">hiddenLayer</span><span class="o">);</span>
<span class="n">listBuilder</span><span class="o">.</span><span class="na">layer</span><span class="o">(</span><span class="mi">2</span><span class="o">,</span> <span class="n">outputLayer</span><span class="o">);</span></code></pre></figure>

<p>Additionally, enable backpropagation by adding the following code:</p>

<figure class="highlight"><pre><code class="language-java" data-lang="java"><span class="n">listBuilder</span><span class="o">.</span><span class="na">backprop</span><span class="o">(</span><span class="kc">true</span><span class="o">);</span></code></pre></figure>

<p>At this point, we can generate and initialize our neural network as an instance of the <code class="highlighter-rouge">MultiLayerNetwork</code> class.</p>

<figure class="highlight"><pre><code class="language-java" data-lang="java"><span class="n">MultiLayerNetwork</span> <span class="n">myNetwork</span> <span class="o">=</span> <span class="k">new</span> <span class="n">MultiLayerNetwork</span><span class="o">(</span><span class="n">listBuilder</span><span class="o">.</span><span class="na">build</span><span class="o">());</span>
<span class="n">myNetwork</span><span class="o">.</span><span class="na">init</span><span class="o">();</span></code></pre></figure>

<h3 id="creating-training-data">Creating Training Data</h3>

<p>To create our training data, we’ll be using the <code class="highlighter-rouge">INDArray</code> class, which is provided by ND4J. Here’s what our training data will look like:</p>

<div class="highlighter-rouge"><pre class="highlight"><code>INPUTS      EXPECTED OUTPUTS
------      ----------------
0,0         0
0,1         1
1,0         1
1,1         0
</code></pre>
</div>

<p>As you might have guessed, our neural network will behave like an XOR gate. Our training data has four samples, and you must mention it in your code:</p>

<figure class="highlight"><pre><code class="language-java" data-lang="java"><span class="kd">final</span> <span class="kt">int</span> <span class="n">NUM_SAMPLES</span> <span class="o">=</span> <span class="mi">4</span><span class="o">;</span></code></pre></figure>

<p>And now, create two <code class="highlighter-rouge">INDArray</code> objects for the inputs and expected outputs, and initialize them with zeroes.</p>

<figure class="highlight"><pre><code class="language-java" data-lang="java"><span class="n">INDArray</span> <span class="n">trainingInputs</span> <span class="o">=</span> <span class="n">Nd4j</span><span class="o">.</span><span class="na">zeros</span><span class="o">(</span><span class="n">NUM_SAMPLES</span><span class="o">,</span> <span class="n">inputLayer</span><span class="o">.</span><span class="na">getNIn</span><span class="o">());</span>
<span class="n">INDArray</span> <span class="n">trainingOutputs</span> <span class="o">=</span> <span class="n">Nd4j</span><span class="o">.</span><span class="na">zeros</span><span class="o">(</span><span class="n">NUM_SAMPLES</span><span class="o">,</span> <span class="n">outputLayer</span><span class="o">.</span><span class="na">getNOut</span><span class="o">());</span></code></pre></figure>

<p>Note that the number of columns in the inputs array is equal to the number of neurons in the input layer. Similarly, the number of columns in the outputs array is equal to the number of neurons in the output layer.</p>

<p>Filling those arrays with your training data is easy. Just use the <code class="highlighter-rouge">putScalar()</code> method:</p>

<figure class="highlight"><pre><code class="language-java" data-lang="java"><span class="c1">// If 0,0 show 0</span>
<span class="n">trainingInputs</span><span class="o">.</span><span class="na">putScalar</span><span class="o">(</span><span class="k">new</span> <span class="kt">int</span><span class="o">[]{</span><span class="mi">0</span><span class="o">,</span><span class="mi">0</span><span class="o">},</span> <span class="mi">0</span><span class="o">);</span>
<span class="n">trainingInputs</span><span class="o">.</span><span class="na">putScalar</span><span class="o">(</span><span class="k">new</span> <span class="kt">int</span><span class="o">[]{</span><span class="mi">0</span><span class="o">,</span><span class="mi">1</span><span class="o">},</span> <span class="mi">0</span><span class="o">);</span>
<span class="n">trainingOutputs</span><span class="o">.</span><span class="na">putScalar</span><span class="o">(</span><span class="k">new</span> <span class="kt">int</span><span class="o">[]{</span><span class="mi">0</span><span class="o">,</span><span class="mi">0</span><span class="o">},</span> <span class="mi">0</span><span class="o">);</span>

<span class="c1">// If 0,1 show 1</span>
<span class="n">trainingInputs</span><span class="o">.</span><span class="na">putScalar</span><span class="o">(</span><span class="k">new</span> <span class="kt">int</span><span class="o">[]{</span><span class="mi">1</span><span class="o">,</span><span class="mi">0</span><span class="o">},</span> <span class="mi">0</span><span class="o">);</span>
<span class="n">trainingInputs</span><span class="o">.</span><span class="na">putScalar</span><span class="o">(</span><span class="k">new</span> <span class="kt">int</span><span class="o">[]{</span><span class="mi">1</span><span class="o">,</span><span class="mi">1</span><span class="o">},</span> <span class="mi">1</span><span class="o">);</span>
<span class="n">trainingOutputs</span><span class="o">.</span><span class="na">putScalar</span><span class="o">(</span><span class="k">new</span> <span class="kt">int</span><span class="o">[]{</span><span class="mi">1</span><span class="o">,</span><span class="mi">0</span><span class="o">},</span> <span class="mi">1</span><span class="o">);</span>

<span class="c1">// If 1,0 show 1</span>
<span class="n">trainingInputs</span><span class="o">.</span><span class="na">putScalar</span><span class="o">(</span><span class="k">new</span> <span class="kt">int</span><span class="o">[]{</span><span class="mi">2</span><span class="o">,</span><span class="mi">0</span><span class="o">},</span> <span class="mi">1</span><span class="o">);</span>
<span class="n">trainingInputs</span><span class="o">.</span><span class="na">putScalar</span><span class="o">(</span><span class="k">new</span> <span class="kt">int</span><span class="o">[]{</span><span class="mi">2</span><span class="o">,</span><span class="mi">1</span><span class="o">},</span> <span class="mi">0</span><span class="o">);</span>
<span class="n">trainingOutputs</span><span class="o">.</span><span class="na">putScalar</span><span class="o">(</span><span class="k">new</span> <span class="kt">int</span><span class="o">[]{</span><span class="mi">2</span><span class="o">,</span><span class="mi">0</span><span class="o">},</span> <span class="mi">1</span><span class="o">);</span>

<span class="c1">// If 1,1 show 0</span>
<span class="n">trainingInputs</span><span class="o">.</span><span class="na">putScalar</span><span class="o">(</span><span class="k">new</span> <span class="kt">int</span><span class="o">[]{</span><span class="mi">3</span><span class="o">,</span><span class="mi">0</span><span class="o">},</span> <span class="mi">1</span><span class="o">);</span>
<span class="n">trainingInputs</span><span class="o">.</span><span class="na">putScalar</span><span class="o">(</span><span class="k">new</span> <span class="kt">int</span><span class="o">[]{</span><span class="mi">3</span><span class="o">,</span><span class="mi">1</span><span class="o">},</span> <span class="mi">1</span><span class="o">);</span>
<span class="n">trainingOutputs</span><span class="o">.</span><span class="na">putScalar</span><span class="o">(</span><span class="k">new</span> <span class="kt">int</span><span class="o">[]{</span><span class="mi">3</span><span class="o">,</span><span class="mi">0</span><span class="o">},</span> <span class="mi">0</span><span class="o">);</span></code></pre></figure>

<p>Our neural network won’t be using the <code class="highlighter-rouge">INDArray</code> objects directly. Therefore, convert them into a <code class="highlighter-rouge">DataSet</code>.</p>

<figure class="highlight"><pre><code class="language-java" data-lang="java"><span class="n">DataSet</span> <span class="n">myData</span> <span class="o">=</span> <span class="k">new</span> <span class="n">DataSet</span><span class="o">(</span><span class="n">trainingInputs</span><span class="o">,</span> <span class="n">trainingOutputs</span><span class="o">);</span></code></pre></figure>

<p>Finally, to start the training, call the <code class="highlighter-rouge">fit()</code> method of the neural network and pass the data set to it:</p>

<figure class="highlight"><pre><code class="language-java" data-lang="java"><span class="n">myNetwork</span><span class="o">.</span><span class="na">fit</span><span class="o">(</span><span class="n">myData</span><span class="o">);</span></code></pre></figure>

<p>And that’s all there is to it. Your neural network is ready to be used.</p>

<h3 id="conclusion">Conclusion</h3>

<p>In this tutorial, you saw how easy it is to create and train a neural network using the Deeplearning4J library in an Android Studio project. I’d like to warn you, however, that training a neural network on a low-powered, battery operated device might not alway be a good idea.</p>

<h4 id="related-reading">Related Reading</h4>

<ul>
  <li><a href="/2016/09/how-to-create-and-use-neural-networks-in-javascript.html">How to Create Simple Neural Networks in JavaScript</a></li>
  <li><a href="/2016/09/how-to-create-deep-neural-networks-in-javascript.html">How to Create Deep Neural Networks in JavaScript</a></li>
</ul>

                    </div>

                    <!-- Share -->
                    <div class="post-share">
                        <p>If you found this article useful, please share it with your friends and colleagues!</p>
                        <a class="btn btn-primary" style="background:#4099FF" target="_blank" href="https://twitter.com/intent/tweet?text=How to Use Deeplearning4J in Android Apps&url=http://progur.com/2017/01/how-to-use-deeplearning4j-on-android.html&via=hathibel" onclick="javascript:window.open(this.href,
  '', 'menubar=no,toolbar=no,resizable=yes,scrollbars=yes,height=450,width=600');return false;"><i class="fa fa-twitter fa-lg"></i></a>

                        <a class="btn btn-primary" style="background:#3b5998" target="_blank" href="https://facebook.com/sharer.php?u=http://progur.com/2017/01/how-to-use-deeplearning4j-on-android.html" onclick="javascript:window.open(this.href,
  '', 'menubar=no,toolbar=no,resizable=yes,scrollbars=yes,height=450,width=600');return false;"><i class="fa fa-facebook fa-lg"></i></a>
                        
                        <a class="btn btn-primary" style="background:#dd4b39" target="_blank" href="https://plus.google.com/share?url=http://progur.com/2017/01/how-to-use-deeplearning4j-on-android.html" onclick="javascript:window.open(this.href,
  '', 'menubar=no,toolbar=no,resizable=yes,scrollbars=yes,height=600,width=600');return false;"><i class="fa fa-google-plus fa-lg"></i></a>
                    </div>

                    <!-- End of Share -->

                    <!-- Comments -->
                      <div class="comments">
                          <div id="disqus_thread"></div>
                            <script>                                    
                                var disqus_config = function () {
                                    this.page.url = "http://progur.com/2017/01/how-to-use-deeplearning4j-on-android.html";
                                    this.page.identifier = "/2017/01/how-to-use-deeplearning4j-on-android.html";
                                };
                                (function() {
                                    var d = document, s = d.createElement('script');
                                    s.src = '//progur.disqus.com/embed.js';
                                    s.setAttribute('data-timestamp', +new Date());
                                    (d.head || d.body).appendChild(s);
                                })();
                            </script>
                            <noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>
                      </div>
                    <!-- End of comments -->
                </div>
            </div>
        </div>
    </div>
</div>

<footer class="footer">
  <div class="container">
    <p>
        Copyright &copy; 2016-2017 Progur.com | All rights reserved.
        <br/>
        Powered by Jekyll, and several secret sauces.
    </p>
  </div>
</footer>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>

          <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/SyntaxHighlighter/3.0.83/scripts/shAutoloader.min.js"></script>
          <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/SyntaxHighlighter/3.0.83/scripts/shCore.min.js"></script>
          <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/SyntaxHighlighter/3.0.83/scripts/shBrushBash.min.js"></script>
          <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/SyntaxHighlighter/3.0.83/scripts/shBrushJava.min.js"></script>
          <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/SyntaxHighlighter/3.0.83/scripts/shBrushPython.min.js"></script>
          <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/SyntaxHighlighter/3.0.83/scripts/shBrushXml.min.js"></script>
          <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/SyntaxHighlighter/3.0.83/scripts/shBrushRuby.min.js"></script>
          <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/SyntaxHighlighter/3.0.83/scripts/shBrushCpp.min.js"></script>
          <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/SyntaxHighlighter/3.0.83/scripts/shBrushJScript.min.js"></script>

          <script>
              SyntaxHighlighter.defaults.toolbar = false;
              SyntaxHighlighter.all();
          </script>

  </body>
</html>