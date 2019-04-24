---
title: 'Návod: Kompilování programu C++/CLI na příkazovém řádku'
ms.date: 09/24/2018
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
ms.openlocfilehash: c90d2c915db7264dc1b4e4807803e063c2a24fc7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314166"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Návod: Kompilování programu C++/CLI na příkazovém řádku

Můžete vytvořit programů aplikace Visual C++, které cílí Common Language Runtime (CLR) a pomocí rozhraní .NET Framework a sestavení na příkazovém řádku. Vizuální C++ podporuje C++/CLI programovací jazyk, který obsahuje operátory a další typy cílit na .NET programovací model. Obecné informace o C++vyhodnocovací jazyka naleznete v tématu [programování v rozhraní .NET s C++vyhodnocovací (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

V tomto názorném postupu použijete k vytvoření základního textového editoru C++vyhodnocovací programu a jeho následnou kompilaci v příkazovém řádku. (Můžete použít vlastní C++/program rozhraní příkazového řádku místo zadání ten, který se zobrazí, nebo můžete použít C++vyhodnocovací vzorového kódu z jiného článku nápovědy. Tato technika je užitečná pro vytváření a testování malé moduly, které mají bez prvků uživatelského rozhraní.)

## <a name="prerequisites"></a>Požadavky

Rozumíte základům jazyka C++.

## <a name="compiling-a-ccli-program"></a>Kompilování C++vyhodnocovací programu

Následující kroky ukazují, jak sestavit C++vyhodnocovací konzolovou aplikaci využívající tříd rozhraní .NET Framework.

Povolit kompilace pro C++/rozhraní příkazového řádku, je nutné použít [/CLR](reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru. Kompilátor MSVC generuje soubor .exe, který obsahuje kód jazyka MSIL – nebo smíšený jazyk MSIL i nativní kód – a odkazy na požadované knihovny rozhraní .NET Framework.

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>Chcete-li zkompilovat C++vyhodnocovací aplikace v příkazovém řádku

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
[Projekty a systémy sestavení](projects-and-build-systems-cpp.md)<br/>
[Parametry kompilátoru MSVC](reference/compiler-options.md)
