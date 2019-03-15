---
title: 'Průvodce: Kompilování programu C++/CX na příkazovém řádku'
ms.date: 09/24/2018
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: ad718a2eb876430d7721d0cd20cfd5b952750f8b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809506"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>Návod: Kompilování programu C++/CX na příkazovém řádku

Můžete vytvořit programy v jazyce Visual C++, které se zaměřují na modul Windows Runtime je v příkazovém řádku. Jazyk Visual C++ podporuje rozšíření součásti Visual C++ (C + +/ CX), který má další typy a operátory cílení programovacího modelu Windows Runtime. Můžete použít C + +/ CX a vytvářejte aplikace pro univerzální platformu Windows (UPW), Windows Phone 8.1 a Windows desktop. Další informace najdete v tématu [A prohlídku vyhodnocování +/ CX](https://msdn.microsoft.com/magazine/dn166929.aspx) a [přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md).

V tomto názorném postupu pomocí textového editoru, vytvořte základní C + +/ CX programu a jeho následnou kompilaci v příkazovém řádku. (Můžete použít vlastní C + +/ CX program místo zadání ten, který se zobrazí, nebo můžete použít C + +/ CX vzorového kódu z jiného článku nápovědy. Tato technika je užitečná pro vytváření a testování malé moduly, které mají bez prvků uživatelského rozhraní.)

> [!NOTE]
> Můžete také integrovaného vývojového prostředí sady Visual Studio ke kompilaci C + +/ CX programy. Integrované vývojové prostředí zahrnuje návrhu, ladění, emulace a podpoře nasazení, která není k dispozici v příkazovém řádku, a proto doporučujeme použít integrovaného vývojového prostředí pro vytváření aplikací univerzální platformy Windows (UPW). Další informace najdete v tématu [vytvoření aplikace pro UPW v jazyce C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

## <a name="prerequisites"></a>Požadavky

Rozumíte základům jazyka C++.

## <a name="compiling-a-ccx-program"></a>Kompilace jazyka C + +/ CX programu

Chcete-li povolit kompilace pro C + +/ CX, je nutné použít [/ZW](reference/zw-windows-runtime-compilation.md) – možnost kompilátoru. Kompilátor MSVC generuje soubor .exe, zaměřuje na modul Windows Runtime, který obsahuje odkazy na požadované knihovny.

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>Chcete-li zkompilovat a C + +/ CX aplikace v příkazovém řádku

1. Otevřít **Developer Command Prompt** okna. (Na **Start** otevřené okno **aplikace**. Otevřít **Visual Studio Tools** ve složce vaší verze sady Visual Studio a klikněte na tlačítko **Developer Command Prompt** zástupce.) Další informace o tom, jak otevřít okno příkazového řádku pro vývojáře najdete v tématu [použít MSVC nástrojů z příkazového řádku](building-on-the-command-line.md).

   Přihlašovací údaje správce, může být nutné úspěšně kompilaci kódu, v závislosti na operačním systému a konfigurace počítače. Chcete-li spustit okno příkazového řádku jako správce, otevřete místní nabídku pro **Developer Command Prompt** a klikněte na tlačítko **spustit jako správce**.

1. Na příkazovém řádku zadejte **Poznámkový blok basiccx.cpp**.

   Zvolte **Ano** Jakmile budete vyzváni k vytvoření souboru.

1. V programu Poznámkový blok zadejte tyto řádky:

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. V panelu nabídky zvolte **souboru** > **Uložit**.

   Vytvoření zdrojového souboru jazyka Visual C++, který používá prostředí Windows Runtime [Platform – obor názvů](../cppcx/platform-namespace-c-cx.md) oboru názvů.

1. Na příkazovém řádku zadejte **/Link /ZW basiccx.cpp cl/EHsc/Subsystem: Console**. Cl.exe – kompilátor zkompiluje zdrojový kód do souboru .obj a pak spustí linkeru, aby generoval spustitelný program s názvem basiccx.exe. ( [/EHsc](reference/eh-exception-handling-model.md) – možnost kompilátoru Určuje model zpracování výjimek jazyka C++ a [/link](reference/link-pass-options-to-linker.md) příznak určuje konzolové aplikace.)

1. Chcete-li spustit basiccx.exe program příkazového řádku, zadejte **basiccx**.

   Program zobrazí tento text a ukončení:

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>Viz také:

[Projekty a sestavení systémy](projects-and-build-systems-cpp.md)<br/>
[Možnosti kompilátoru MSVC](reference/compiler-options.md)
