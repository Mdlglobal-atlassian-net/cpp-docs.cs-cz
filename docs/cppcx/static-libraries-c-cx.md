---
title: Statické knihovny (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 3c4bfd28b805903a2e596ef6d648ff31b0b8261c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358100"
---
# <a name="static-libraries-ccx"></a>Statické knihovny (C++/CX)

Statická knihovna používaná v aplikaci univerzální platformy Windows (UPW) může obsahovat kód standardu ISO, včetně typů STL, a také volání oken Win32, která nejsou vyloučena z platformy aplikace Prostředí Windows Runtime. Statická knihovna spotřebovává součásti prostředí Windows Runtime a může vytvářet součásti prostředí Windows Runtime s určitými omezeními.

## <a name="creating-static-libraries"></a>Vytváření statických knihoven

Pokyny pro vytvoření nového projektu se liší v závislosti na verzi sady Visual Studio, kterou jste nainstalovali. Chcete-li zobrazit dokumentaci k upřednostňované verzi sady Visual Studio, použijte ovládací prvek pro výběr **verze.** Nachází se v horní části obsahu na této stránce.

::: moniker range="vs-2019"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>Vytvoření statické knihovny UPW v sadě Visual Studio 2019

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu** a otevřete dialogové okno Vytvořit **nový projekt.**

1. V horní části dialogového okna nastavte **jazyk** na **C++**, nastavte **platformu** na **Windows**a nastavte **typ projektu** na **UPW**.

1. Z filtrovaného seznamu typů projektů zvolte **Statická knihovna (Universal Windows - C++/CX)** a pak zvolte **Další**. Na další stránce pojmenujte projekt a v případě potřeby určete umístění projektu.

1. Chcete-li vytvořit projekt, zvolte tlačítko **Vytvořit.**

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>Vytvoření statické knihovny UPW v sadě Visual Studio 2017 nebo Visual Studio 2015

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**. V **části Visual C++** > **Windows Universal** zvolte Static **Library (Universal Windows)**.

1. V **Průzkumníku řešení**otevřete místní nabídku projektu a zvolte **Vlastnosti**. V dialogovém okně **Vlastnosti** nastavte na stránce **Vlastnosti** > konfigurace**C/C++** **možnost Spotřebovat rozšíření prostředí Windows Runtime** na **Ano (/ZW).**

::: moniker-end

Při kompilaci nové statické knihovny, pokud provedete volání rozhraní API Win32, které je vyloučeno pro aplikace UPW, kompilátor vyvolá chybu C3861, "Identifikátor nebyl nalezen." Chcete-li vyhledat alternativní metodu podporovanou pro prostředí Windows Runtime, přečtěte [si téma Alternativy k windowsovým chybám API v aplikacích UPW](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Pokud přidáte projekt statické knihovny C++ do řešení aplikace UPW, bude pravděpodobně muset aktualizovat nastavení vlastností projektu knihovny tak, aby vlastnost podpory UPW byla nastavena na **hodnotu Ano**. Bez tohoto nastavení se kód vytvoří a propojí, ale při pokusu o ověření aplikace pro Microsoft Store dojde k chybě. Statické lib by měly být kompilovány se stejným nastavením kompilátoru jako projekt, který spotřebovává.

Pokud spotřebováváte statickou knihovnu, která vytváří veřejné `ref` třídy, třídy veřejného rozhraní nebo třídy veřejných hodnot, propojovací zařízení vyvolá toto upozornění:

> **upozornění LNK4264:** archivace souboru objektu zkompilovaného pomocí /ZW do statické knihovny; Všimněte si, že při vytváření typů prostředí Windows Runtime se nedoporučuje propojit se statickou knihovnou, která obsahuje metadata prostředí Windows Runtime.

Upozornění můžete bezpečně ignorovat pouze v případě, že statická knihovna nevytváří součásti prostředí Windows Runtime, které jsou spotřebovány mimo samotnou knihovnu. Pokud knihovna nespotřebovává součást, která definuje, pak propojovací služba můžete optimalizovat pryč implementace i v případě, že veřejná metadata obsahuje informace o typu. To znamená, že veřejné součásti ve statické knihovně se zkompilují, ale neaktivují se za běhu. Z tohoto důvodu musí být všechny součásti prostředí Windows Runtime určené ke spotřebě jinými součástmi nebo aplikacemi implementovány v dynamické knihovně (DLL).

## <a name="see-also"></a>Viz také

[Dělení do vláken a zařazování](../cppcx/threading-and-marshaling-c-cx.md)
