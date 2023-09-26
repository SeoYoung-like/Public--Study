**[ 스냅샷, 스톱워치 ]**

* 스냅샷 사용법이랑 스톱워치 사용법 숙지하자!



COMP 1500 - CodeSample - 10 - StringConcatVsStringBuilder

※ 스톱모션 사용하는 법 익혀서 나중에 여러가지 실험해 볼 것!

```csharp
using System;
using System.Diagnostics;
using System.Text;

namespace StringConcatVsStringBuilder
{
    class Program
    {
        static void Main(string[] args)
        {
            const int LOOP_COUNT = 1000;

            Stopwatch stopWatch = new Stopwatch();

            #region USING_CONCATENATION
            stopWatch.Start();

            string concatenated = string.Empty;
            for (int i = 0; i < LOOP_COUNT; i++)
            {
                concatenated += "test";
            }

            stopWatch.Stop();
            Console.WriteLine($"Time elapsed in ms (Concatenated): {stopWatch.Elapsed.TotalMilliseconds}");
            #endregion

            stopWatch.Reset();

            #region USING_STRING_BUILDER
            stopWatch.Start();

            StringBuilder stringBuilder = new StringBuilder(4096);
            for (int i = 0; i < LOOP_COUNT; i++)
            {
                stringBuilder.Append("test");
            }

            string s = stringBuilder.ToString();

            stopWatch.Stop();
            Console.WriteLine($"Time elapsed in ms (StringBuilder): {stopWatch.Elapsed.TotalMilliseconds}");
            #endregion
        }
    }
}
```

* https://pocu-ko.teachable.com/courses/719491/lectures/13045637

* https://slides.pocu.academy/ko/Courses/COMP1500/Lectures/10#/2?_k=afvmwa