---
title: "marK is (still) evolving"
date: "2020-09-07"
coverImage: "screenshot_20200907_125518.png"
---

Over the last year, I have lost my ability to blog frequently about my code contributions and there has been around 1.5 years since my last post about marK. If you don't know what marK is, please read the mentioned post here:

- [marK – Starting the Development of a General Purpose Tool for Data Annotation](https://caiojcarvalho.wordpress.com/2019/01/29/mark-a-general-purpose-tool-for-data-annotation/)

In the meantime, a lot of things have happened. Now the project has an official [KDE repository](https://invent.kde.org/education/mark) and I have been working with [Jean Andrade (jyeno)](https://jyeno.home.blog/) on some improvements, trying to include more interesting features for a release.

I have improved its GUI, so it is completely different from what you have seen in my previous post. Of course, it still needs some fixes and we need to change some parts of the GUI to be compatible with KF5, but now we have an idea of how marK is going to show its files, options, etc.

![](https://caiojcarvalho.files.wordpress.com/2020/09/ezgif-6-ea82cfaf0d99.png?w=1024)

_Now we can train an AI model to detect Konqis on images, haha._ :)

Jean has worked on marK during [Season of KDE](https://community.kde.org/SoK/2020/StatusReport/Jean_Lima_Andrade) and [Google Summer of Code](https://community.kde.org/GSoC/2020/StatusReports/JeanLimaAndrade). During SoK, he has helped on some code refactoring and has implemented important features related to image annotation such as the XML/JSON import/export process and temporary files.

_Example of XML exported file:_

<annotation>
  <object>
    <class>konqi</class>
    <Polygon>
      <pt>
        <x>616</x>
        <y>325</y>
      </pt>
      ...
      <pt>
        <x>616</x>
        <y>325</y>
      </pt>
    </Polygon>
  </object>
</annotation>

_Example of JSON exported file:_

\[
  {
    "Class": "konqi",
    "Polygon": \[
      {
        "pt": {
          "x": "616",
          "y": "325"
        }
      },
      ...
      {
        "pt": {
          "x": "616",
          "y": "325"
        }
      }
    \]
  }
\]

I have worked on improving marK architecture, so now we have a Painter structure to help on dealing with different types of data in the Container widget. During GSoC, Jean has worked on implementing text support, which allow you to annotate textual datasets for natural language processing tasks.

![](https://caiojcarvalho.files.wordpress.com/2020/09/sem-titulo.png?w=1024)

_Text annotation support._

We are currently working on some bug fixes to prepare it for a release (I hope so). See you soon!
