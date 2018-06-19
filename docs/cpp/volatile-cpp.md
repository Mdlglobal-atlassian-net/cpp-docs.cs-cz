---
title: volatile (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- volatile_cpp
dev_langs:
- C++
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 295654586a3fe251526a4764d54f80f3a70c7014
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423951"
---
# <a name="volatile-c"></a>volatile (C++)
Kvalifikátor typu, můžete použít k deklaraci, že objekt mohou být upravena v programu hardwaru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
volatile declarator ;  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) přepínače kompilátoru upravit jak kompilátor interpretuje toto klíčové slovo.  
  
 Visual Studio interpretuje `volatile` – klíčové slovo odlišně v závislosti na architektuře cíl. Pro ARM, pokud žádné **/volatile** – možnost kompilátoru je zadána, provede kompilátor jako **/volatile:iso** byly zadány. Pro architektury než ARM, pokud žádné **/volatile** – možnost kompilátoru je zadána, provede kompilátor jako **/volatile:ms** byly zadány; proto pro architektury důrazně jsme jiné než ARM Doporučujeme, který zadáte **/volatile:iso**a použijte explicitní synchronizace primitiv a vnitřní funkce kompilátoru, když pracujete s pamětí, který je sdílen mezi vláken.  
  
 Můžete použít `volatile` kvalifikátor poskytnout přístup k umístění v paměti, které se používají asynchronní procesy, například obslužné rutiny přerušení.  
  
 Když `volatile` se používá v proměnné, která má také [__restrict](../cpp/extension-restrict.md) – klíčové slovo, `volatile` přednost.  
  
 Pokud `struct` člen je označena jako `volatile`, pak `volatile` rozšířena do celé struktury. Pokud do struktury nemá délku, která je možné zkopírovat na aktuální architektuře pomocí jedné instrukce `volatile` může být v této struktury úplně ztraceny.  
  
 `volatile` – Klíčové slovo může mít žádný vliv na pole, pokud platí jedna z následujících podmínek:  
  
-   Délka pole volatile překračuje maximální velikost, které lze kopírovat na aktuální architektuře pomocí jedné instrukce.  
  
-   Délka nejkrajnější obsahující `struct`– nebo pokud je členem skupiny může být vnořený `struct`– přesahuje maximální velikost, které lze kopírovat na aktuální architektuře pomocí jedné instrukce.  
  
 I když procesoru není změnit pořadí zrušení Uložitelný paměti přistupuje, bez Uložitelný proměnných musí být označen jako `volatile` zaručit, že kompilátor není změnit pořadí paměť přistupuje.  
  
 Objekty, které jsou deklarovány jako `volatile` nejsou v určité optimalizace použít, protože jejich hodnoty můžete kdykoli změnit.  Systém vždy přečte aktuální hodnota volatile objektu na vyžádání, i v případě, že předchozí instrukce žádali hodnotu ze stejného objektu.  Hodnota objektu je navíc okamžitě zapisují na přiřazení.  
  
## <a name="iso-compliant"></a>ISO kompatibilní  
 Pokud jste obeznámeni s C# volatile – klíčové slovo nebo obeznámeni s chováním `volatile` v dřívějších verzích systému Visual C++, mějte na paměti, C ++ 11 ISO standardní `volatile` – klíčové slovo se liší a je podporována v sadě Visual Studio při [/ volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md) – možnost kompilátoru je zadán. (Pro ARM, jeho hodnota je určena ve výchozím nastavení). `volatile` – Klíčové slovo v C ++ 11 ISO standardní kódu má být použita pouze pro přístup k hardwaru; nepoužívejte ho pro komunikaci mezi vlákno. Pro komunikaci mezi vlákno, použijte mechanismy pro [std::atomic\<T >](../standard-library/atomic.md) z [standardní knihovna C++](../standard-library/cpp-standard-library-reference.md).  
  
## <a name="end-of-iso-compliant"></a>Konec ISO kompatibilní  
  
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Když **/volatile:ms** – možnost kompilátoru slouží – ve výchozím nastavení, pokud jsou cílem architektury než ARM – kompilátor generuje navíc kód Udržovat řazení mezi odkazy k nestálým objektům kromě zachování řazení na odkazy na další globální objekty. Zejména:  
  
-   Zápis na objekt volatile (také označované jako volatile zápis) má verzi sémantiku; To znamená odkaz na globální nebo statické objekt, který se nachází před zápis na objekt volatile v pořadí instrukce dojde před této volatile zápisu v kompilovaném binárního souboru.  
  
-   Čtení objektu volatile (také označované jako volatile pro čtení) má získání sémantiku; odkaz na globální nebo statické objekt, který nastane po čtení volatile paměti v pořadí instrukce tedy dojde po přečtení tohoto volatile v kompilovaném binárního souboru.  
  
 To umožňuje nestálé objekty, které má být použit pro zámky paměti a verzí v vícevláknové aplikace.  
  
> [!NOTE]
>  Když přitom spoléhá na rozšířené záruka, že když poskytl **/volatile:ms** – možnost kompilátoru se používá, kód je jiný přenositelností.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Const](../cpp/const-cpp.md)   
 [Ukazatelé const a volatile](../cpp/const-and-volatile-pointers.md)