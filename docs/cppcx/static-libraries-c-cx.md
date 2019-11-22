---
title: Statické knihovny (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: f62ef03cfdf2f424fd4a50c2e866d73b5bdce7fc
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302941"
---
# <a name="static-libraries-ccx"></a>Statické knihovny (C++/CX)

Statická knihovna, která se používá v aplikaci Univerzální platforma Windows (UWP), může obsahovat kód ISO standard C++ , včetně typů STL, a také volání rozhraní API systému Win32, která nejsou vyloučena z aplikace prostředí Windows Runtime App Platform. Statická knihovna spotřebovává prostředí Windows Runtime komponenty a může vytvářet prostředí Windows Runtime komponenty s určitými omezeními.

## <a name="creating-static-libraries"></a>Vytváření statických knihoven


Pokyny pro vytvoření nového projektu se liší v závislosti na verzi sady Visual Studio, kterou jste nainstalovali. Ujistěte se, že máte selektor verzí v levém horním rohu nastavený na správnou verzi.

::: moniker range="vs-2019"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>Vytvoření statické knihovny UWP v aplikaci Visual Studio 2019

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt** . otevře se dialogové okno **vytvořit nový projekt** .

1. V horní části dialogového okna nastavte **jazyk** na **C++** , nastavte **platformu** na **Windows**a jako **typ projektu** nastavte na **UWP**. 

1. Z filtrovaného seznamu typů projektů zvolte možnost **Statická knihovna (Universal Windows- C++/CX)** a pak klikněte na tlačítko **Další**. Na další stránce zadejte název projektu a v případě potřeby určete umístění projektu.

1. Kliknutím na tlačítko **vytvořit** vytvořte projekt.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>Vytvoření statické knihovny UWP v aplikaci Visual Studio 2017 nebo Visual Studio 2015

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu**. V **části C++ Visual** > **Windows Universal** zvolit **statickou knihovnu (Universal Windows)** .

1. V **Průzkumník řešení**otevřete místní nabídku pro projekt a poté zvolte možnost **vlastnosti**. V dialogovém okně **vlastnosti** na stránce **Vlastnosti konfigurace** > **CC++ nebo** nastavte **rozšíření spotřebovávat prostředí Windows Runtime** na **Ano (/ZW)** .

::: moniker-end

Při kompilaci nové statické knihovny, pokud provedete volání Win32 API vyloučeného pro aplikace pro UWP, kompilátor vyvolá chybu C3861, identifikátor nebyl nalezen. Alternativní metodu, která je pro prostředí Windows Runtime podporovaná, najdete [v tématu alternativy k rozhraním API Windows v aplikacích pro UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Pokud přidáte projekt C++ statické knihovny do řešení aplikace UWP, bude pravděpodobně nutné aktualizovat nastavení vlastnosti projektu knihovny tak, aby byla vlastnost podpora UWP nastavena na **hodnotu Ano**. Bez tohoto nastavení kód vytvoří a propojí, ale při pokusu o ověření aplikace pro Microsoft Store dojde k chybě. Statická knihovna lib by měla být zkompilována se stejným nastavením kompilátoru jako projekt, který ho využívá.

Použijete-li statickou knihovnu, která vytvoří veřejné třídy `ref`, třídy veřejných rozhraní nebo veřejné třídy hodnot, linker toto upozornění vyvolá:

> **Upozornění LNK4264:** archivace souboru objektu zkompilovaného pomocí/ZW do statické knihovny; Pamatujte, že při vytváření prostředí Windows Runtime typů se nedoporučuje propojit se statickou knihovnou, která obsahuje prostředí Windows Runtime metadata.

Upozornění lze bezpečně ignorovat pouze v případě, že Statická knihovna neprodukuje prostředí Windows Runtime komponenty, které jsou spotřebovány mimo samotnou knihovnu. Pokud knihovna nevyužívá komponentu, kterou definuje, pak linker může optimalizovat implementaci, i když veřejná metadata obsahují informace o typu. To znamená, že veřejné součásti ve statické knihovně budou kompilovány, ale za běhu se neaktivují. Z tohoto důvodu musí být všechny prostředí Windows Runtime komponenty určené pro použití jinými komponentami nebo aplikacemi implementovány v dynamické knihovně (DLL).

## <a name="see-also"></a>Viz také:

[Dělení do vláken a zařazování](../cppcx/threading-and-marshaling-c-cx.md)
