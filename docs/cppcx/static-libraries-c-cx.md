---
title: "Statické knihovny (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 5f86d24c693cfcd5eecf8b37f0e4567c9c7af3a0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="static-libraries-ccx"></a>Statické knihovny (C + +/ CX)
Statické knihovny, který se používá v aplikaci pro univerzální platformu Windows může obsahovat kód ISO standard C++, včetně typů STL a také volání rozhraní API Win32, které nejsou vyloučené z aplikační platforma univerzální platformu Windows. Statické knihovny využívá komponenty prostředí Windows Runtime a může vytvořit komponenty prostředí Windows Runtime s určitými omezeními.  
  
## <a name="creating-static-libraries"></a>Vytvoření statické knihovny  
  
#### <a name="to-create-a-static-library-for-use-in-a-universal-windows-platform-app"></a>Chcete-li vytvořit statickou knihovnu pro použití v aplikaci pro univerzální platformu Windows  
  
1.  Na řádku nabídek zvolte **soubor** > **nový** > **projektu** > **prázdné statické knihovny** pro Universal Windows Platform apps.  
  
2.  V **Průzkumníku řešení**, otevřete místní nabídky projektu a zvolte **vlastnosti**. V **vlastnosti** v dialogovém **vlastnosti konfigurace** > **Obecné** nastavte podpora aplikací pro univerzální platformu Windows  **Ano**.  
  
3.  Na **vlastnosti konfigurace** > **C/C++** nastavte **spotřebě** prostředí Windows Runtime **rozšíření** k **Ano (/ZW)**.  
  
 Když zkompilujete novou statickou knihovnu, pokud provedete volání Win32 API, která je vyloučená pro univerzální platformu Windows aplikace, kompilátor dosáhne chyby C3861, "Identifikátor nebyl nalezen." Vyhledejte alternativní metoda, která je podporována pro prostředí Windows Runtime, najdete v tématu [alternativy k rozhraní API systému Windows v aplikacích pro Windows Store](http://msdn.microsoft.com/en-us/75568012-61e0-41cc-a4df-c698f54f21ec).  
  
 Pokud přidáte projektu statické knihovny jazyka C++ na řešení aplikace univerzální platformu Windows, bude pravděpodobně nutné aktualizovat nastavení vlastností projektu knihovny, tak, aby vlastnost podporu univerzální platformu Windows je nastavena na **Ano**. Bez tohoto nastavení kód sestaví a odkazy, ale k chybě dochází při pokusu o ověření pro aplikaci [!INCLUDE[win8_appstore_long](../cppcx/includes/win8-appstore-long-md.md)]. Statické lib má kompilovat s stejné nastavení kompilátoru jako projekt, který využívá ho.  
  
 Pokud využívat statickou knihovnu, která vytvoří veřejné `ref` tříd, veřejné rozhraní a třídy hodnota veřejného linkeru vyvolá toto upozornění:  
  
> **upozornění LNK4264:** archivaci souboru objektu kompilovat s /ZW do statické knihovny; Všimněte si, že při vytváření prostředí Windows Runtime typy není doporučeno propojit s statickou knihovnu, která obsahuje metadata prostředí Windows Runtime.  
  
 Můžete bezpečně ignorovat upozornění pouze v případě, že se statickou knihovnou neprodukuje prostředí Windows Runtime součásti, které se spotřebovávají mimo samotné knihovny. Pokud knihovny nebude využívat komponenty, která definuje, pak linkeru optimalizovat můžete rychle implementace to i v případě, že veřejný metadata obsahují informace o typu. To znamená, že veřejný součásti v statické knihovny bude kompilovat, ale nebude aktivovat za běhu. Z tohoto důvodu musí být v dynamické knihovně (DLL) implementované jakékoli prostředí Windows Runtime součásti, která je určená pro používání jiné součásti nebo aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Dělení na vlákna a zařazování](../cppcx/threading-and-marshaling-c-cx.md)