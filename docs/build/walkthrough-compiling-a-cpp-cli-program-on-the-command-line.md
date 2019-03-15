---
title: 'Průvodce: Kompilování programu C++/CLI na příkazovém řádku'
ms.date: 09/24/2018
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
ms.openlocfilehash: c90d2c915db7264dc1b4e4807803e063c2a24fc7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811924"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Návod: Kompilování programu C++/CLI na příkazovém řádku

Můžete vytvořit programů aplikace Visual C++, které cílí Common Language Runtime (CLR) a pomocí rozhraní .NET Framework a sestavení na příkazovém řádku. Jazyk Visual C++ podporuje C + +/ CLI programovací jazyk, který obsahuje operátory a další typy cílit na .NET programovací model. Obecné informace o jazyce C + +/ jazyce CLI, najdete v článku [.NET programování v jazyce C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

V tomto názorném postupu pomocí textového editoru, vytvořte základní C + +/ CLI programu a jeho následnou kompilaci v příkazovém řádku. (Můžete použít vlastní C + +/ CLI program místo zadání ten, který se zobrazí, nebo můžete použít C + +/ CLI vzorového kódu z jiného článku nápovědy. Tato technika je užitečná pro vytváření a testování malé moduly, které mají bez prvků uživatelského rozhraní.)

## <a name="prerequisites"></a>Požadavky

Rozumíte základům jazyka C++.

## <a name="compiling-a-ccli-program"></a>Kompilace jazyka C + +/ CLI programu

Následující kroky ukazují, jak kompilovat a C + +/ CLI konzolovou aplikaci využívající tříd rozhraní .NET Framework.

Povolit kompilace pro C + +/ CLI, je nutné použít [/CLR](reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru. Kompilátor MSVC generuje soubor .exe, který obsahuje kód jazyka MSIL – nebo smíšený jazyk MSIL i nativní kód – a odkazy na požadované knihovny rozhraní .NET Framework.

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>Chcete-li zkompilovat a C + +/ CLI aplikace v příkazovém řádku

1. Otevřít **Developer Command Prompt** okna. Konkrétní pokyny najdete v tématu [otevřete okno příkazového řádku pro vývojáře](building-on-the-command-line.md#developer_command_prompt).

   Přihlašovací údaje správce, může být nutné úspěšně kompilaci kódu, v závislosti na operačním systému a konfigurace počítače. Spusťte okno příkazového řádku jako správce, kliknete pravým tlačítkem na otevřete místní nabídku pro příkazový řádek a klikněte na tlačítko **Další** > **spustit jako správce**.

1. Na příkazovém řádku zadejte `notepad basicclr.cpp`.

   Zvolte **Ano** Jakmile budete vyzváni k vytvoření souboru.

1. V programu Poznámkový blok zadejte tyto řádky:

   ```cpp
   int main()
   {
       System::Console::WriteLine("This is a C++/CLI program.");
   }
   ```

1. V panelu nabídky zvolte **souboru** > **Uložit**.

   Vytvoření zdrojového souboru jazyka Visual C++, který používá třídu rozhraní .NET Framework (<xref:System.Console>) v <xref:System> oboru názvů.

1. Na příkazovém řádku zadejte `cl /clr basicclr.cpp`. Cl.exe – kompilátor zkompiluje zdrojový kód do souboru .obj, který obsahuje jazyk MSIL a pak spustí linkeru, aby generoval spustitelný program s názvem basicclr.exe.

1. Chcete-li spustit basicclr.exe program příkazového řádku, zadejte `basicclr`.

   Program zobrazí tento text a ukončení:

   ```Output
   This is a C++/CLI program.
   ```

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Projekty a sestavení systémy](projects-and-build-systems-cpp.md)<br/>
[Možnosti kompilátoru MSVC](reference/compiler-options.md)
