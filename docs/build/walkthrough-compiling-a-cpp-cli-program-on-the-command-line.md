---
title: 'Návod: Kompilace programu C++/CLI v příkazovém řádku'
ms.date: 04/23/2019
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
ms.openlocfilehash: 8a5c5659367350a80725b365ef9c431bbec209d1
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877458"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Návod: Kompilace programu C++/CLI v příkazovém řádku

Můžete vytvořit Visual C++ programy, které cílí na modul CLR (Common Language Runtime), a použít .NET Framework a sestavit je na příkazovém řádku. Visual C++ podporuje programovací jazyk C++/CLI, který obsahuje další typy a operátory pro cílení programovacího modelu .NET. Obecné informace o jazyce C++/CLI naleznete v tématu [programování .NET s C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

V tomto návodu použijete textový editor k vytvoření základního programu C++/CLI a potom ho zkompilujete na příkazovém řádku. (Můžete použít vlastní program C++/CLI namísto psaní ovládacího prvku, který je zobrazen, nebo můžete použít ukázku kódu jazyka C++/CLI z jiného článku s článkem help. Tato technika je užitečná pro vytváření a testování malých modulů, které nemají žádné prvky uživatelského rozhraní.)

## <a name="prerequisites"></a>Požadavky

Rozumíte základům jazyka C++.

## <a name="compiling-a-ccli-program"></a>Kompilování programu C++/CLI

Následující kroky ukazují, jak zkompilovat konzolovou aplikaci C++/CLI, která používá .NET Framework třídy.

Chcete-li povolit kompilaci pro jazyk C++/CLI, je nutné použít možnost kompilátoru [/CLR](reference/clr-common-language-runtime-compilation.md) . Kompilátor MSVC generuje soubor. exe, který obsahuje kód jazyka MSIL, nebo smíšený jazyk MSIL a nativní kód – a odkazuje na požadované knihovny .NET Framework.

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>Kompilace aplikace C++/CLI na příkazovém řádku

1. Otevřete **Developer Command Prompt** okno. Konkrétní pokyny najdete v tématu [otevření okna příkazového řádku pro vývojáře](building-on-the-command-line.md#developer_command_prompt).

   Pověření správce může být vyžadováno pro úspěšné kompilování kódu v závislosti na operačním systému a konfiguraci počítače. Chcete-li spustit okno příkazového řádku jako správce, klikněte pravým tlačítkem myši a otevřete místní nabídku pro příkazový řádek a pak zvolte možnost **Další** > **Spustit jako správce**.

1. Do příkazového řádku zadejte `notepad basicclr.cpp`.

   Po zobrazení výzvy k vytvoření souboru vyberte **Ano** .

1. V programu Poznámkový blok zadejte tyto řádky:

   ```cpp
   int main()
   {
       System::Console::WriteLine("This is a C++/CLI program.");
   }
   ```

1. Na řádku nabídek klikněte na Uložit **soubor** > **Save**.

   Vytvořili jste zdrojový soubor Visual C++, který v<xref:System.Console> <xref:System> oboru názvů používá třídu .NET Framework ().

1. Do příkazového řádku zadejte `cl /clr basicclr.cpp`. Kompilátor cl. exe zkompiluje zdrojový kód do souboru. obj, který obsahuje jazyk MSIL a poté spustí linker pro vygenerování spustitelného programu s názvem basicclr. exe.

1. Chcete-li spustit program basicclr. exe, zadejte `basicclr`do příkazového řádku.

   Program zobrazí tento text a ukončí:

   ```Output
   This is a C++/CLI program.
   ```

## <a name="see-also"></a>Viz také

[Reference jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a systémy sestavení](projects-and-build-systems-cpp.md)<br/>
[Parametry kompilátoru MSVC](reference/compiler-options.md)
