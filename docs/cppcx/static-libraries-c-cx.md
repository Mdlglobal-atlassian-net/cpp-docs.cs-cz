---
title: Statické knihovny (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 188ba06518bf6cdd154b7d6bd61216ed1e4ffad3
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877244"
---
# <a name="static-libraries-ccx"></a>Statické knihovny (C++/CX)

Statické knihovny, který se používá v aplikaci pro univerzální platformu Windows (UPW) může obsahovat kód jazyka C++ podle standardu ISO, včetně typů STL a volání rozhraní API Win32, které nejsou vyloučeny z aplikace platformy Windows Runtime. Statická knihovna spotřebovává součásti prostředí Windows Runtime a může vytvářet komponenty prostředí Windows Runtime s určitými omezeními.

## <a name="creating-static-libraries"></a>Vytvoření statické knihovny


Pokyny pro vytvoření nového projektu se liší v závislosti na tom, kterou verzi sady Visual Studio jste nainstalovali. Ujistěte se, že máte volič verze v horním vlevo nastavené na správné verzi.

::: moniker range="vs-2019"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>Chcete-li vytvořit statickou knihovnu UPW v aplikaci Visual Studio 2019

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu** otevřít **vytvořte nový projekt** dialogové okno.

1. V horní části dialogového okna, nastavte **jazyk** k **C++**, nastavte **platformy** k **Windows**a nastavte **typprojektu** k **UPW**. 

1. Filtrované seznamu typů projektů zvolte **statická knihovna (Universal Windows - C++/CX)** klikněte na tlačítko **Další**. Na další stránce zadejte název projektu a zadejte umístění projektu, v případě potřeby.

1. Zvolte **vytvořit** tlačítko pro vytvoření projektu.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>Chcete-li vytvořit statickou knihovnu UWP v sadě Visual Studio 2017 nebo Visual Studio 2015

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu**. V části **Visual C++** > **Windows Universal** zvolte **statická knihovna (Universal Windows)**.

1. V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **vlastnosti**. V **vlastnosti** dialogovém okně **vlastnosti konfigurace** > **C/C++** nastavte **využívat rozšíření modulu Runtime Windows** k **Ano (/ZW)**.

::: moniker-end

Při kompilaci novou statickou knihovnu, pokud provedete voláním rozhraní Win32 API, která je vyloučená pro aplikace pro UPW, kompilátor vyvolá chybu C3861, "Identifikátor se nenašel." Vyhledejte alternativní metodu, která je podporována pro prostředí Windows Runtime, najdete v článku [alternativy k rozhraní API Windows v aplikacích pro UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Pokud chcete přidat projekt statické knihovny C++ do řešení aplikace UPW, bude pravděpodobně nutné aktualizovat nastavení vlastností projektu knihovny, tak, aby je nastavena podpora UWP, na **Ano**. Bez tohoto nastavení dojde k sestavení kódu a odkazy, ale k chybě dojde při pokusu o ověření aplikace pro Microsoft Store. Statické knihovny lib by měl být zkompilován pomocí stejného nastavení kompilátoru jako projekt, který je spotřebovává.

Pokud využíváte statickou knihovnu, která vytvoří veřejné `ref` tříd, veřejné rozhraní a třídy hodnota veřejného linker vydá toto varování:

> **upozornění LNK4264:** zkompiloval s parametrem /ZW do statické knihovny; soubor objektu archivace mějte na paměti, že při vytváření typů prostředí Windows Runtime nedoporučuje propojení se statickou knihovnou, která obsahuje metadata prostředí Windows Runtime.

Upozornění můžete bezpečně ignorovat pouze v případě, že se statickou knihovnou není vytváření komponent Windows Runtime, využívání mimo samotné knihovny. Pokud knihovny nespotřeboval komponenty, která definuje, pak linkeru můžete optimalizují implementace i v případě, že veřejný metadata obsahují informace o typu. To znamená, že bude zkompilována veřejné součásti ve statické knihovně, ale za běhu, neaktivuje. Z tohoto důvodu všechny modulu Windows Runtime komponenty, která je určena pro použití jinými součástmi nebo aplikace musí být implementován v dynamická knihovna (DLL).

## <a name="see-also"></a>Viz také:

[Dělení do vláken a zařazování](../cppcx/threading-and-marshaling-c-cx.md)
