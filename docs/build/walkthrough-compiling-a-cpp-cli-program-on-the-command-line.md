---
title: 'Návod: Kompilace C + +/ CLI Program na příkazovém řádku | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 46e4b8d6341ad659596f7e83ab3cdcb89b18df2d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705303"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Návod: Kompilace C + +/ CLI Program na příkazovém řádku

Můžete vytvořit programy Visual C++, cíle Common Language Runtime (CLR), které používají rozhraní .NET Framework a sestavení je na příkazovém řádku. Podporuje Visual C++ C + +/ CLI programovací jazyk, který má operátory a další typy, jehož cílem je programovací model rozhraní .NET. Obecné informace o jazyce C + +/ CLI jazyka, najdete v části [.NET programování v jazyce C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

V tomto názorném postupu získáte pomocí textového editoru k vytvoření základní C + +/ CLI programu a zkompilujte jej na příkazovém řádku. (Můžete použít vlastní C + +/ CLI program místo zadání ten, který se zobrazí, nebo můžete použít C + +/ CLI ukázka kódu z jiný článek nápovědy. Tato metoda je užitečná pro vytváření a testování malé modulů, které obsahují žádné elementy uživatelského rozhraní.)

> [!NOTE]
> Můžete také použít Visual Studio IDE zkompilovat C + +/ CLI programy. Další informace najdete v tématu [návod: kompilace programu C++ pro CLR v sadě Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md).

## <a name="prerequisites"></a>Požadavky

Je potřeba pochopit základy jazyka C++.

## <a name="compiling-a-ccli-program"></a>Kompilování C + +/ CLI programu

Následující kroky ukazují, jak zkompilovat C + +/ CLI konzolovou aplikaci, která používá třídy rozhraní .NET Framework.

Chcete-li povolit kompilace pro C + +/ CLI, je nutné použít [/CLR](../build/reference/clr-common-language-runtime-compilation.md) – možnost kompilátoru. Visual C++ compiler generuje soubor .exe, který obsahuje kód MSIL – nebo ve smíšeném MSIL a nativní kód – a odkazy na požadované knihovny rozhraní .NET Framework.

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>Kompilace C + +/ CLI aplikace na příkazovém řádku

1. Otevřete **příkazový řádek vývojáře** okno. Konkrétní pokyny najdete v tématu [otevřete okno příkazového řádku vývojáře](../build/building-on-the-command-line.md#developer_command_prompt).

   Přihlašovací údaje správce může být nutné úspěšně zkompilovat kód, v závislosti na operačním systému a konfigurace počítače. Spusťte okno příkazového řádku jako správce, kliknete pravým tlačítkem na otevření místní nabídky pro příkazový řádek a potom vyberte **Další**, **spustit jako správce**.

1. Na příkazovém řádku zadejte **Poznámkový blok basicclr.cpp**.

   Zvolte **Ano** po zobrazení výzvy k vytvoření souboru.

1. V poznámkovém bloku zadejte tyto řádky:

   ```cpp
   int main()
   {
       System::Console::WriteLine("This is a C++/CLI program.");
   }
   ```

1. Na řádku nabídek zvolte **soubor**, **Uložit**.

   Jste vytvořili Visual C++ zdrojový soubor, který používá třídu rozhraní .NET Framework (<xref:System.Console>) v <xref:System> oboru názvů.

1. Na příkazovém řádku zadejte **cl/CLR basicclr.cpp**. Cl.exe – kompilátor zkompiluje zdrojový kód do souboru .obj, který obsahuje MSIL a poté spustí linkeru pro generování spustitelný program s názvem basicclr.exe.

1. Chcete-li basicclr.exe program, spusťte na příkazovém řádku, zadejte **basicclr**.

   Program zobrazí tento text a bude ukončen:

   ```Output
   This is a C++/CLI program.
   ```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)
- [Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)
- [Možnosti kompilátoru](../build/reference/compiler-options.md)
