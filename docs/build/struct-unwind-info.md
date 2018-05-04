---
title: struktura UNWIND_INFO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f0aee906-a1b9-44cc-a8ad-463637bd5411
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 14b17a79905ffc7814e2aecf92e90f3db526453f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="struct-unwindinfo"></a>struct UNWIND_INFO
Informace o struktuře unwind dat se používá k zaznamenání účinků funkce, která má ukazatel na zásobník a kde jsou uloženy nezávislé registry v zásobníku:  
  
|||  
|-|-|  
|UBYTE: 3|Version|  
|UBYTE: 5|Příznaky|  
|UBYTE|Velikost prologu|  
|UBYTE|Počet unwind kódů|  
|UBYTE: 4|Rámec registru|  
|UBYTE: 4|Posun rámce registru (rozšířená)|  
|Ushort – * n|Pole unwind kódů|  
|proměnná|Lze buď formuláře (1) nebo (2) níže|  
  
 (1) obslužná rutina výjimky  
  
|||  
|-|-|  
|ULONG –|Adresa obslužná rutina výjimky|  
|proměnná|Obslužné rutiny pro konkrétní jazyk data (volitelné)|  
  
 (2) zřetězené Unwind Info  
  
|||  
|-|-|  
|ULONG –|Počáteční adresa funkce|  
|ULONG –|Koncová adresa funkce|  
|ULONG –|Adresa unwind info|  
  
 Struktura UNWIND_INFO musí být typu DWORD v paměti. Význam každé pole je následující:  
  
 **Verze**  
 Číslo verze unwind dat, aktuálně 1.  
  
 **Příznaky**  
 Aktuálně jsou definovány tři příznaky:  
  
 UNW_FLAG_EHANDLER Funkce má obslužnou rutinu výjimky, která by měla být volána při vyhledávání pro funkce, které potřebují k zjištění výjimek.  
  
 UNW_FLAG_UHANDLER Funkce má obslužné rutiny ukončení, která by měla být volána, když unwinding výjimku.  
  
 UNW_FLAG_CHAININFO unwind info struktura není primární jeden postup. Zřetězené unwind místo toho informace, že položka je obsah předchozí položky RUNTIME_FUNCTION. Zobrazí se následující text vysvětlení zřetězené struktury unwind info. Pokud je nastavený tento příznak, je potřeba smazat příznaky UNW_FLAG_EHANDLER a UNW_FLAG_UHANDLER. Pole rámce registrace a -stack přidělení navíc musí mít stejné hodnoty jako primární unwind info.  
  
 **Velikost prologu**  
 Délka funkce prologu v bajtech.  
  
 **Počet unwind kódů**  
 Toto je počet patic v unwind kódů. Všimněte si, že některé unwind kódy (například UWOP_SAVE_NONVOL) vyžadují více než jeden slot v poli.  
  
 **Rámec registru**  
 Pokud nenulové hodnoty, potom funkce používá ukazatel na rámec a toto pole je počet stálý registr použít jako ukazatel rámečku, pomocí stejné kódování pro pole informace o operaci UNWIND_CODE uzlů.  
  
 **Posun (škálovat) registru rámce**  
 Pokud je pole rámce registru nenulové, to je měřítko posunu z konfigurace, který se použije pro FP reg, když se zjistí. Skutečný FP reg je nastaven na možnost konfigurace a 16 * toto číslo, což umožňuje posun od 0 do 240. To umožňuje odkazující FP reg do středu přidělení místní zásobníku pro dynamický rámec zásobníku, umožňující lepší hustoty kódu prostřednictvím kratší pokyny (Další pokyny můžete použít podepsaný posunutí tvaru 8bitové).  
  
 **Pole unwind kódů**  
 Toto je pole položek, které popisují účinek prologu na stálé registry a konfigurace. Najdete v části na UNWIND_CODE význam jednotlivých položek. Pro účely zarovnání bude mít toto pole vždy sudý počet položek s potenciálně nepoužívanou závěrečnou položkou (v takovém případě pole bude jeden déle, než je uvedeno podle počtu pole unwind kódů).  
  
 **Adresa obslužná rutina výjimky**  
 To je ukazatel relativní bitové kopie do obslužné rutiny funkce pro konkrétní jazyk výjimky nebo ukončení (Pokud je příznak UNW_FLAG_CHAININFO zrušte a jeden z příznaků UNW_FLAG_EHANDLER nebo UNW_FLAG_UHANDLER je nastavena).  
  
 **Data obslužné rutiny pro konkrétní jazyk**  
 Jedná se o data obslužné rutiny výjimek specifické pro jazyk funkce. Formát tato data je neurčené a kompletně určen obslužná rutina výjimky konkrétní používán.  
  
 **Zřetězené Unwind Info**  
 Pokud je nastavený příznak UNW_FLAG_CHAININFO Struktura UNWIND_INFO končí se třemi UWORD.  Tyto UWORD představují RUNTIME_FUNCTION informace pro funkci zřetězené unwind.  
  
## <a name="see-also"></a>Viz také  
 [Unwind data pro zpracování výjimek, podpora ladění](../build/unwind-data-for-exception-handling-debugger-support.md)