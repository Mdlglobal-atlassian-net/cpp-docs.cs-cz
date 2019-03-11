---
title: Statické knihovny (C + +/ CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 242ba10b29a8efe0c3e9580f1d0d0c3be529a7d2
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738931"
---
# <a name="static-libraries-ccx"></a>Statické knihovny (C + +/ CX)

Statické knihovny, který se používá v aplikaci pro univerzální platformu Windows (UPW) může obsahovat kód jazyka C++ podle standardu ISO, včetně typů STL a volání rozhraní API Win32, které nejsou vyloučeny z aplikace platformy Windows Runtime. Statická knihovna spotřebovává součásti prostředí Windows Runtime a může vytvářet komponenty prostředí Windows Runtime s určitými omezeními.

## <a name="creating-static-libraries"></a>Vytvoření statické knihovny

#### <a name="to-create-a-static-library-for-use-in-a-uwp-app"></a>Vytvoření statické knihovny pro použití v aplikaci UWP

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu**. V části **Visual C++** > **Windows Universal** zvolte **statická knihovna (Universal Windows)**.

1. V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **vlastnosti**. V **vlastnosti** dialogovém okně **vlastnosti konfigurace** > **C/C++** nastavte **využívat rozšíření modulu Runtime Windows** k **Ano (/ZW)**.

Při kompilaci novou statickou knihovnu, pokud provedete voláním rozhraní Win32 API, která je vyloučená pro aplikace pro UPW, kompilátor vyvolá chybu C3861, "Identifikátor se nenašel." Vyhledejte alternativní metodu, která je podporována pro prostředí Windows Runtime, najdete v článku [alternativy k rozhraní API Windows v aplikacích pro UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Pokud chcete přidat projekt statické knihovny C++ do řešení aplikace UPW, bude pravděpodobně nutné aktualizovat nastavení vlastností projektu knihovny, tak, aby je nastavena podpora UWP, na **Ano**. Bez tohoto nastavení dojde k sestavení kódu a odkazy, ale k chybě dojde při pokusu o ověření aplikace pro Microsoft Store. Statické knihovny lib by měl být zkompilován pomocí stejného nastavení kompilátoru jako projekt, který je spotřebovává.

Pokud využíváte statickou knihovnu, která vytvoří veřejné `ref` tříd, veřejné rozhraní a třídy hodnota veřejného linker vydá toto varování:

> **upozornění LNK4264:** zkompiloval s parametrem /ZW do statické knihovny; soubor objektu archivace mějte na paměti, že při vytváření typů prostředí Windows Runtime nedoporučuje propojení se statickou knihovnou, která obsahuje metadata prostředí Windows Runtime.

Upozornění můžete bezpečně ignorovat pouze v případě, že se statickou knihovnou není vytváření komponent Windows Runtime, využívání mimo samotné knihovny. Pokud knihovny nespotřeboval komponenty, která definuje, pak linkeru můžete optimalizují implementace i v případě, že veřejný metadata obsahují informace o typu. To znamená, že bude zkompilována veřejné součásti ve statické knihovně, ale za běhu, neaktivuje. Z tohoto důvodu všechny modulu Windows Runtime komponenty, která je určena pro použití jinými součástmi nebo aplikace musí být implementován v dynamická knihovna (DLL).

## <a name="see-also"></a>Viz také:

[Práce s vlákny a zařazování](../cppcx/threading-and-marshaling-c-cx.md)
