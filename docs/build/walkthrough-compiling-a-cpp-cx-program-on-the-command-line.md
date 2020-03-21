---
title: 'Návod: kompilace programu C++/CX na příkazovém řádku'
ms.date: 04/23/2019
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: 83369fc7b458463ea1f44a347bbcd0ca4eb32224
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078210"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>Návod: kompilace programu C++/CX na příkazovém řádku

> [!NOTE]
> Pro nové aplikace a komponenty UWP doporučujeme používat [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), standardní projekci jazyka c++ 17 pro rozhraní API pro prostředí Windows Runtime. C++/WinRT je k dispozici v sadě Windows 10 SDK od verze 1803 další. C++/WinRT je implementováno zcela v hlavičkových souborech a je navrženo tak, aby vám poskytovala prvotřídní přístup k modernímu rozhraní Windows API.

Kompilátor Microsoft C++ (MSVC) podporuje C++ rozšíření komponent (C++/CX), které má další typy a operátory pro cílení na prostředí Windows Runtime programovací model. Pro sestavování aplikací pro Univerzální platforma Windows (UWP) a Desktop Windows můžete použít C++/CX. Další informace najdete v tématu [prohlídka rozhraní C++/CX](https://msdn.microsoft.com/magazine/dn166929.aspx) a [rozšíření komponent pro běhové platformy](../extensions/component-extensions-for-runtime-platforms.md).

V tomto návodu použijete textový editor k vytvoření základního C++programu/CX a potom ho zkompilujete na příkazovém řádku. (Můžete použít vlastní C++program/CX namísto psaní ovládacího prvku, který je zobrazen, nebo můžete použít ukázku kódu C++/CX z jiného článku Help. Tato technika je užitečná pro vytváření a testování malých modulů, které nemají žádné prvky uživatelského rozhraní.)

> [!NOTE]
> Můžete také použít integrované vývojové prostředí (IDE) sady C++Visual Studio k kompilování programů/CX. Vzhledem k tomu, že IDE zahrnuje návrh, ladění, emulaci a podporu nasazení, které nejsou k dispozici na příkazovém řádku, doporučujeme, abyste k sestavování aplikací Univerzální platforma Windows (UWP) použili integrované vývojové prostředí (IDE). Další informace najdete v tématu [Vytvoření aplikace pro UWP v C++ ](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

## <a name="prerequisites"></a>Předpoklady

Rozumíte základům tohoto C++ jazyka.

## <a name="compiling-a-ccx-program"></a>Kompilování C++programu/CX

Chcete-li povolit C++kompilaci pro/CX, je nutné použít možnost kompilátoru [/ZW](reference/zw-windows-runtime-compilation.md) . Kompilátor MSVC vygeneruje soubor. exe, který cílí na prostředí Windows Runtime a odkazuje na požadované knihovny.

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>Kompilace aplikace C++/CX na příkazovém řádku

1. Otevřete **Developer Command Prompt** okno. (V okně **Start** otevřete **aplikace**. Otevřete složku **Visual Studio Tools** ve vaší verzi sady Visual Studio a pak zvolte zástupce **Developer Command Prompt** .) Další informace o tom, jak otevřít okno Developer Command Prompt, naleznete v tématu [použití sady nástrojů MSVC z příkazového řádku](building-on-the-command-line.md).

   Pověření správce může být vyžadováno pro úspěšné kompilování kódu v závislosti na operačním systému a konfiguraci počítače. Chcete-li spustit okno příkazového řádku jako správce, otevřete místní nabídku pro **Developer Command Prompt** a pak zvolte možnost **Spustit jako správce**.

1. Na příkazovém řádku zadejte **Poznámkový blok basiccx. cpp**.

   Po zobrazení výzvy k vytvoření souboru vyberte **Ano** .

1. V programu Poznámkový blok zadejte tyto řádky:

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. Na panelu nabídek vyberte **soubor** > **Uložit**.

   Vytvořili jste C++ zdrojový soubor, který používá obor názvů prostředí Windows Runtime [platformy](../cppcx/platform-namespace-c-cx.md) .

1. Do příkazového řádku zadejte **CL/EHSC/ZW basiccx. cpp/Link/SUBSYSTEM: Console**. Kompilátor cl. exe zkompiluje zdrojový kód do souboru. obj a potom spustí linker, který vygeneruje spustitelný program s názvem basiccx. exe. (Možnost kompilátoru [/EHsc](reference/eh-exception-handling-model.md) určuje model zpracování C++ výjimek a příznak [/Link](reference/link-pass-options-to-linker.md) určuje konzolovou aplikaci.)

1. Chcete-li spustit program basiccx. exe, zadejte na příkazovém řádku **basiccx**.

   Program zobrazí tento text a ukončí:

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>Viz také

[Projekty a systémy sestavení](projects-and-build-systems-cpp.md)<br/>
[Parametry kompilátoru MSVC](reference/compiler-options.md)
