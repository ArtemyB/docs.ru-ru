---
title: "Директивы компилятора (F#)"
description: "Дополнительные сведения о F # язык директивы препроцессора, директивы условной компиляции, строки директивы и директивы компилятора."
keywords: "visual f#, f#, функциональное программирование"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 93aef07a-6747-4ce4-a10f-a05168978af6
ms.openlocfilehash: b4305d24163f9b23631d5efb6e838f55127cd9f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="compiler-directives"></a><span data-ttu-id="6577a-104">Директивы компилятора</span><span class="sxs-lookup"><span data-stu-id="6577a-104">Compiler Directives</span></span>

<span data-ttu-id="6577a-105">В этом разделе описываются директивы процессора и директивы компилятора.</span><span class="sxs-lookup"><span data-stu-id="6577a-105">This topic describes processor directives and compiler directives.</span></span>


## <a name="preprocessor-directives"></a><span data-ttu-id="6577a-106">Директивы препроцессора</span><span class="sxs-lookup"><span data-stu-id="6577a-106">Preprocessor Directives</span></span>
<span data-ttu-id="6577a-107">Директива препроцессора дополняется префиксом с символом «#» и отображается в строке сама по себе.</span><span class="sxs-lookup"><span data-stu-id="6577a-107">A preprocessor directive is prefixed with the # symbol and appears on a line by itself.</span></span> <span data-ttu-id="6577a-108">Она интерпретируется препроцессором, который запускается перед самим компилятором.</span><span class="sxs-lookup"><span data-stu-id="6577a-108">It is interpreted by the preprocessor, which runs before the compiler itself.</span></span>

<span data-ttu-id="6577a-109">В следующей таблице перечислены директивы препроцессора, имеющиеся в F#.</span><span class="sxs-lookup"><span data-stu-id="6577a-109">The following table lists the preprocessor directives that are available in F#.</span></span>


|<span data-ttu-id="6577a-110">Директива</span><span class="sxs-lookup"><span data-stu-id="6577a-110">Directive</span></span>|<span data-ttu-id="6577a-111">Описание</span><span class="sxs-lookup"><span data-stu-id="6577a-111">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="6577a-112">`#if`*символ*</span><span class="sxs-lookup"><span data-stu-id="6577a-112">`#if` *symbol*</span></span>|<span data-ttu-id="6577a-113">Поддерживает условную компиляцию.</span><span class="sxs-lookup"><span data-stu-id="6577a-113">Supports conditional compilation.</span></span> <span data-ttu-id="6577a-114">Код в разделе после `#if` включается, если *символ* определен.</span><span class="sxs-lookup"><span data-stu-id="6577a-114">Code in the section after the `#if` is included if the *symbol* is defined.</span></span>|
|`#else`|<span data-ttu-id="6577a-115">Поддерживает условную компиляцию.</span><span class="sxs-lookup"><span data-stu-id="6577a-115">Supports conditional compilation.</span></span> <span data-ttu-id="6577a-116">Помечает раздел кода, который следует включить, если символ, используемый с предыдущей директивой `#if`, не определен.</span><span class="sxs-lookup"><span data-stu-id="6577a-116">Marks a section of code to include if the symbol used with the previous `#if` is not defined.</span></span>|
|`#endif`|<span data-ttu-id="6577a-117">Поддерживает условную компиляцию.</span><span class="sxs-lookup"><span data-stu-id="6577a-117">Supports conditional compilation.</span></span> <span data-ttu-id="6577a-118">Помечает конец условного раздела кода.</span><span class="sxs-lookup"><span data-stu-id="6577a-118">Marks the end of a conditional section of code.</span></span>|
|<span data-ttu-id="6577a-119">`#`[строка] *int*,</span><span class="sxs-lookup"><span data-stu-id="6577a-119">`#`[line] *int*,</span></span><br/><span data-ttu-id="6577a-120">`#`[строка] *int* *строка*,</span><span class="sxs-lookup"><span data-stu-id="6577a-120">`#`[line] *int* *string*,</span></span><br/><span data-ttu-id="6577a-121">`#`[строка] *int* *буквальная строка*</span><span class="sxs-lookup"><span data-stu-id="6577a-121">`#`[line] *int* *verbatim-string*</span></span>|<span data-ttu-id="6577a-122">Указывает исходную строку кода и имя файла для отладки.</span><span class="sxs-lookup"><span data-stu-id="6577a-122">Indicates the original source code line and file name, for debugging.</span></span> <span data-ttu-id="6577a-123">Эта возможность предназначена для средств, создающих исходный код F#.</span><span class="sxs-lookup"><span data-stu-id="6577a-123">This feature is provided for tools that generate F# source code.</span></span>|
|<span data-ttu-id="6577a-124">`#nowarn`*warningcode*</span><span class="sxs-lookup"><span data-stu-id="6577a-124">`#nowarn` *warningcode*</span></span>|<span data-ttu-id="6577a-125">Отключает предупреждение или предупреждения компилятора.</span><span class="sxs-lookup"><span data-stu-id="6577a-125">Disables a compiler warning or warnings.</span></span> <span data-ttu-id="6577a-126">Чтобы отключить предупреждение, найдите его номер в выходных данных компилятора и заключите его в кавычки.</span><span class="sxs-lookup"><span data-stu-id="6577a-126">To disable a warning, find its number from the compiler output and include it in quotation marks.</span></span> <span data-ttu-id="6577a-127">Не указывайте префикс «FS».</span><span class="sxs-lookup"><span data-stu-id="6577a-127">Omit the "FS" prefix.</span></span> <span data-ttu-id="6577a-128">Чтобы отключить несколько номеров предупреждений в одной строке, заключите каждый номер в кавычки и отделяйте каждую строку пробелом.</span><span class="sxs-lookup"><span data-stu-id="6577a-128">To disable multiple warning numbers on the same line, include each number in quotation marks, and separate each string by a space.</span></span> <span data-ttu-id="6577a-129">Пример:</span><span class="sxs-lookup"><span data-stu-id="6577a-129">For example:</span></span>

`#nowarn "9" "40"`


<span data-ttu-id="6577a-130">Влияние отключения предупреждения применяется файл целиком, включая части файла выше этой директивы. |</span><span class="sxs-lookup"><span data-stu-id="6577a-130">The effect of disabling a warning applies to the entire file, including portions of the file that precede the directive.|</span></span>

## <a name="conditional-compilation-directives"></a><span data-ttu-id="6577a-131">Директивы условной компиляции</span><span class="sxs-lookup"><span data-stu-id="6577a-131">Conditional Compilation Directives</span></span>
<span data-ttu-id="6577a-132">Код, деактивированный одной из этих директив, отображается серым цветом в редакторе Visual StudioCode.</span><span class="sxs-lookup"><span data-stu-id="6577a-132">Code that is deactivated by one of these directives appears dimmed in the Visual StudioCode Editor.</span></span>


>[!NOTE] 
<span data-ttu-id="6577a-133">Поведение директив условной компиляции отличается от их поведения в других языках.</span><span class="sxs-lookup"><span data-stu-id="6577a-133">The behavior of the conditional compilation directives is not the same as it is in other languages.</span></span> <span data-ttu-id="6577a-134">Например, нельзя использовать логические выражения с символами, а `true` и `false` не имеют особого значения.</span><span class="sxs-lookup"><span data-stu-id="6577a-134">For example, you cannot use Boolean expressions involving symbols, and `true` and `false` have no special meaning.</span></span> <span data-ttu-id="6577a-135">Символы, используемые в директиве `if`, должны задаваться с помощью командной строки или в параметрах проекта; в этом языке отсутствует директива препроцессора `define`.</span><span class="sxs-lookup"><span data-stu-id="6577a-135">Symbols that you use in the `if` directive must be defined by the command line or in the project settings; there is no `define` preprocessor directive.</span></span>


<span data-ttu-id="6577a-136">В следующем коде демонстрируется применение директив `#if`, `#else` и `#endif`.</span><span class="sxs-lookup"><span data-stu-id="6577a-136">The following code illustrates the use of the `#if`, `#else`, and `#endif` directives.</span></span> <span data-ttu-id="6577a-137">В данном примере код содержит две версии определения `function1`.</span><span class="sxs-lookup"><span data-stu-id="6577a-137">In this example, the code contains two versions of the definition of `function1`.</span></span> <span data-ttu-id="6577a-138">Когда `VERSION1` определяется с помощью [-define-параметр компилятора](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04), код между `#if` директивы и `#else` активируется.</span><span class="sxs-lookup"><span data-stu-id="6577a-138">When `VERSION1` is defined by using the [-define compiler option](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04), the code between the `#if` directive and the `#else` directive is activated.</span></span> <span data-ttu-id="6577a-139">В противном случае активируется код между директивами `#else` и `#endif`.</span><span class="sxs-lookup"><span data-stu-id="6577a-139">Otherwise, the code between `#else` and `#endif` is activated.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

<span data-ttu-id="6577a-140">В языке F# отсутствует директива препроцессора `#define`.</span><span class="sxs-lookup"><span data-stu-id="6577a-140">There is no `#define` preprocessor directive in F#.</span></span> <span data-ttu-id="6577a-141">Вы должны использовать параметр компилятора или параметры проекта для определения символов, используемых директивой `#if`.</span><span class="sxs-lookup"><span data-stu-id="6577a-141">You must use the compiler option or project settings to define the symbols used by the `#if` directive.</span></span>

<span data-ttu-id="6577a-142">Директивы условной компиляции не могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="6577a-142">Conditional compilation directives can be nested.</span></span> <span data-ttu-id="6577a-143">В директивах препроцессора отступ не важен.</span><span class="sxs-lookup"><span data-stu-id="6577a-143">Indentation is not significant for preprocessor directives.</span></span>


## <a name="line-directives"></a><span data-ttu-id="6577a-144">Директивы строк</span><span class="sxs-lookup"><span data-stu-id="6577a-144">Line Directives</span></span>
<span data-ttu-id="6577a-145">При сборке компилятор сообщает об ошибках в коде F #, ссылаясь на номера строк, в которых возникли ошибки.</span><span class="sxs-lookup"><span data-stu-id="6577a-145">When building, the compiler reports errors in F# code by referencing line numbers on which each error occurs.</span></span> <span data-ttu-id="6577a-146">Номера строк начинаются с 1 для первой строки в файле.</span><span class="sxs-lookup"><span data-stu-id="6577a-146">These line numbers start at 1 for the first line in a file.</span></span> <span data-ttu-id="6577a-147">Тем не менее при создании исходного кода F# из другого средства номера строк в сформированном коде обычно не представляют интереса, поскольку ошибки в сформированном коде F#, скорее всего, проистекают из другого источника.</span><span class="sxs-lookup"><span data-stu-id="6577a-147">However, if you are generating F# source code from another tool, the line numbers in the generated code are generally not of interest, because the errors in the generated F# code most likely arise from another source.</span></span> <span data-ttu-id="6577a-148">Директива `#line` позволяет разработчикам средств, формирующих исходный код F#, передавать сведения о номерах исходных строк и исходных файлах в сформированный код F#.</span><span class="sxs-lookup"><span data-stu-id="6577a-148">The `#line` directive provides a way for authors of tools that generate F# source code to pass information about the original line numbers and source files to the generated F# code.</span></span>

<span data-ttu-id="6577a-149">При использовании директивы `#line` необходимо заключать имена файлов в кавычки.</span><span class="sxs-lookup"><span data-stu-id="6577a-149">When you use the `#line` directive, file names must be enclosed in quotation marks.</span></span> <span data-ttu-id="6577a-150">Если в начале строки не указывается токен verbatim (`@`), то чтобы использовать в пути символы обратной косой черты, необходимо их экранировать, указывая две обратные косые черты вместо одной.</span><span class="sxs-lookup"><span data-stu-id="6577a-150">Unless the verbatim token (`@`) appears in front of the string, you must escape backslash characters by using two backslash characters instead of one in order to use them in the path.</span></span> <span data-ttu-id="6577a-151">Далее приводятся допустимые токены строк.</span><span class="sxs-lookup"><span data-stu-id="6577a-151">The following are valid line tokens.</span></span> <span data-ttu-id="6577a-152">В этих примерах предполагается, что исходный файл `Script1` при запуске в соответствующем средстве приводит к автоматическому созданию файла кода F# и что код в месте расположения этих директив формируется из некоторых токенов в строке 25 файла `Script1`.</span><span class="sxs-lookup"><span data-stu-id="6577a-152">In these examples, assume that the original file `Script1` results in an automatically generated F# code file when it is run through a tool, and that the code at the location of these directives is generated from some tokens at line 25 in file `Script1`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

<span data-ttu-id="6577a-153">Эти токены указывают, что код F#, сформированный в этом месте, является производным от некоторых конструкций в строке `25` или рядом с ней в файле `Script1`.</span><span class="sxs-lookup"><span data-stu-id="6577a-153">These tokens indicate that the F# code generated at this location is derived from some constructs at or near line `25` in `Script1`.</span></span>


## <a name="compiler-directives"></a><span data-ttu-id="6577a-154">Директивы компилятора</span><span class="sxs-lookup"><span data-stu-id="6577a-154">Compiler Directives</span></span>
<span data-ttu-id="6577a-155">Директивы компилятора сходны с директивами препроцессора, поскольку они имеют префикс в виде знака #, но они не интерпретируются препроцессором; компилировать и действовать в соответствии с этими директивами должен компилятор.</span><span class="sxs-lookup"><span data-stu-id="6577a-155">Compiler directives resemble preprocessor directives, because they are prefixed with a # sign, but instead of being interpreted by the preprocessor, they are left for the compiler to interpret and act on.</span></span>

<span data-ttu-id="6577a-156">В следующей таблице перечислены директивы компилятора, доступные в языке F#.</span><span class="sxs-lookup"><span data-stu-id="6577a-156">The following table lists the compiler directive that is available in F#.</span></span>


|<span data-ttu-id="6577a-157">Директива</span><span class="sxs-lookup"><span data-stu-id="6577a-157">Directive</span></span>|<span data-ttu-id="6577a-158">Описание</span><span class="sxs-lookup"><span data-stu-id="6577a-158">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="6577a-159">`#light`[«on»</span><span class="sxs-lookup"><span data-stu-id="6577a-159">`#light` ["on"</span></span>|<span data-ttu-id="6577a-160">«off»]</span><span class="sxs-lookup"><span data-stu-id="6577a-160">"off"]</span></span>|<span data-ttu-id="6577a-161">Включает или отключает упрощенный синтаксис для совместимости с другими версиями ML.</span><span class="sxs-lookup"><span data-stu-id="6577a-161">Enables or disables lightweight syntax, for compatibility with other versions of ML.</span></span> <span data-ttu-id="6577a-162">Упрощенный синтаксис включен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="6577a-162">By default, lightweight syntax is enabled.</span></span> <span data-ttu-id="6577a-163">Подробный синтаксис всегда включен.</span><span class="sxs-lookup"><span data-stu-id="6577a-163">Verbose syntax is always enabled.</span></span> <span data-ttu-id="6577a-164">Таким образом, вы можете использовать как упрощенный, так и подробный синтаксис.</span><span class="sxs-lookup"><span data-stu-id="6577a-164">Therefore, you can use both lightweight syntax and verbose syntax.</span></span> <span data-ttu-id="6577a-165">Директива `#light` сама по себе эквивалентна `#light "on"`.</span><span class="sxs-lookup"><span data-stu-id="6577a-165">The directive `#light` by itself is equivalent to `#light "on"`.</span></span> <span data-ttu-id="6577a-166">Если указана директива `#light "off"`, то для всех языковых конструкций необходимо использовать подробный синтаксис.</span><span class="sxs-lookup"><span data-stu-id="6577a-166">If you specify `#light "off"`, you must use verbose syntax for all language constructs.</span></span> <span data-ttu-id="6577a-167">Синтаксис в документации по F# представлен исходя из предположения, что используется упрощенный синтаксис.</span><span class="sxs-lookup"><span data-stu-id="6577a-167">Syntax in the documentation for F# is presented with the assumption that you are using lightweight syntax.</span></span> <span data-ttu-id="6577a-168">Дополнительные сведения см. в разделе [подробный синтаксис](verbose-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="6577a-168">For more information, see [Verbose Syntax](verbose-syntax.md).</span></span>|
<span data-ttu-id="6577a-169">Директивы интерпретатора (fsi.exe) см. [интерактивного программирование на F #](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="6577a-169">For interpreter (fsi.exe) directives, see [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="6577a-170">См. также</span><span class="sxs-lookup"><span data-stu-id="6577a-170">See Also</span></span>
[<span data-ttu-id="6577a-171">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="6577a-171">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="6577a-172">Параметры компилятора</span><span class="sxs-lookup"><span data-stu-id="6577a-172">Compiler Options</span></span>](compiler-options.md)
