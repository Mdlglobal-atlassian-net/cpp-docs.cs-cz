---
title: Statické knihovny (C + +/ CX) | Microsoft Docs
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ffa905cbe0fd49489bd3634cb927cce57ea4ddbc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090100"
---
# <a name="static-libraries-ccx"></a>Statické knihovny (C + +/ CX)
Statické knihovny, který se používá v aplikaci pro univerzální platformu Windows (UWP) může obsahovat kód ISO standard C++, včetně typů STL a také volání rozhraní API Win32, které nejsou vyloučené z prostředí Windows Runtime aplikační platforma. Statické knihovny využívá komponenty prostředí Windows Runtime a může vytvořit komponenty prostředí Windows Runtime s určitými omezeními.  
  
## <a name="creating-static-libraries"></a>Vytvoření statické knihovny  
  
#### <a name="to-create-a-static-library-for-use-in-a-uwp-app"></a>Chcete-li vytvořit statickou knihovnu pro použití v aplikaci UWP  
  
1.  Na řádku nabídek zvolte **soubor** > **nový** > **projektu**. V části **Visual C++** > **univerzální pro Windows** zvolte **statické knihovny (Universal Windows)**.  
  
2.  V **Průzkumníku řešení**, otevřete místní nabídky projektu a zvolte **vlastnosti**. V **vlastnosti** v dialogovém **vlastnosti konfigurace** > **C/C++** nastavte **využívat Windows Runtime Extension** k **Ano (/ZW)**.  
  
 Když zkompilujete novou statickou knihovnu, pokud provedete volání Win32 API, která je vyloučená pro aplikace UWP, kompilátor dosáhne chyby C3861, "Identifikátor nebyl nalezen." Vyhledejte alternativní metoda, která je podporována pro prostředí Windows Runtime, najdete v tématu [alternativy k rozhraní API systému Windows v aplikacích pro UPW](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).  
  
 Pokud přidáte projektu statické knihovny jazyka C++ na řešení aplikace UPW, bude pravděpodobně nutné aktualizovat nastavení vlastností projektu knihovny, tak, aby vlastnost podporu UWP je nastavena na **Ano**. Bez tohoto nastavení, vytvoří kód a odkazy, ale k chybě dochází při pokusu o ověření aplikace Microsoft Store. Statické lib má kompilovat s stejné nastavení kompilátoru jako projekt, který využívá ho.  
  
 Pokud využívat statickou knihovnu, která vytvoří veřejné `ref` tříd, veřejné rozhraní a třídy hodnota veřejného linkeru vyvolá toto upozornění:  
  
> **upozornění LNK4264:** archivaci souboru objektu kompilovat s /ZW do statické knihovny; Všimněte si, že při vytváření prostředí Windows Runtime typy není doporučeno propojit s statickou knihovnu, která obsahuje metadata prostředí Windows Runtime.  
  
 Můžete bezpečně ignorovat upozornění pouze v případě, že se statickou knihovnou neprodukuje prostředí Windows Runtime součásti, které se spotřebovávají mimo samotné knihovny. Pokud knihovny nebude využívat komponenty, která definuje, pak linkeru optimalizovat můžete rychle implementace to i v případě, že veřejný metadata obsahují informace o typu. To znamená, že veřejný součásti v statické knihovny bude kompilovat, ale nebude aktivovat za běhu. Z tohoto důvodu musí být v dynamické knihovně (DLL) implementované jakékoli prostředí Windows Runtime součásti, která je určená pro používání jiné součásti nebo aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Dělení na vlákna a zařazování](../cppcx/threading-and-marshaling-c-cx.md)