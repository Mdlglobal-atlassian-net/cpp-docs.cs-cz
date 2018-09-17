---
title: UNWIND_INFO – struktura | Dokumentace Microsoftu
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
ms.openlocfilehash: 6b342aa89dd82f89b1318da3ab1acb610085a7e7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717012"
---
# <a name="struct-unwindinfo"></a>struct UNWIND_INFO

Datová struktura informací o uvolnění se používá k zaznamenání efekty, které funkce má ukazatel na zásobník a kde jsou uloženy do zásobníku stálé registry:

|||
|-|-|
|UBYTE: 3|Version|
|UBYTE: 5|Příznaky|
|UBYTE|Velikost kódu prologu|
|UBYTE|Počet kódy unwind|
|UBYTE: 4|Rámec registru|
|UBYTE: 4|Odsazení rámce registr (škálovat)|
|USHORT \* n|Pole kódy unwind|
|proměnná|Buď formuláře (1) nebo (2) níže může být|

(1) obslužná rutina výjimky

|||
|-|-|
|ULONG|Adresa obslužné rutiny výjimek|
|proměnná|Data obslužné rutiny pro konkrétní jazyk (volitelné)|

(2) zřetězené Unwind Info

|||
|-|-|
|ULONG|Počáteční adresa – funkce|
|ULONG|Koncová adresa – funkce|
|ULONG|Adresa unwind info|

UNWIND_INFO struktura musí být typu DWORD v paměti. Význam jednotlivých polí vypadá takto:

- **Verze**

   Číslo verze dat uvolnění nepovedlo aktuálně 1.

- **příznaky**

   Aktuálně jsou definovány tři příznaky:

   |Příznak|Popis|
   |-|-|
   |`UNW_FLAG_EHANDLER`| Funkce má obslužná rutina výjimky, která by měla být volána při vyhledávání pro funkce, které muset zkoumat výjimky.|
   |`UNW_FLAG_UHANDLER`| Funkce má obslužné rutiny ukončení, která by měla být volána při uvolnění výjimku.|
   |`UNW_FLAG_CHAININFO`| Unwind info, že struktura není primární jedné postupem. Zřetězené unwind místo toho informace, že položka je obsah předchozí RUNTIME_FUNCTION položky. Zobrazí se následující text vysvětlení zřetězené struktury unwind info. Pokud je tento příznak nastaven, musí být zrušeno UNW_FLAG_EHANDLER a UNW_FLAG_UHANDLER příznaky. Pole přidělení registru a – zásobník snímků taky, musí mít stejné hodnoty jako primární unwind info.|

- **Velikost kódu prologu**

   Délka sekvence prologu funkce v bajtech.

- **Počet kódy unwind**

   Toto je počet slotů v kódy unwind. Všimněte si, že některé parsovat kódy unwind (například UWOP_SAVE_NONVOL) vyžadují více než jedné pozice v poli.

- **Rámec registru**

   Pokud nenulovou hodnotu, použije funkce na ukazatel na rámec, a toto pole je počet stálé registr používaný jako ukazatel na rámec, pomocí stejné kódování pro pole informace o operaci UNWIND_CODE uzlů.

- **Posun (škálovat) registru rámce**

   Pokud pole rámce registru je nenulová, jedná se škálován posun od RSP, které platí pro FP registru, když se zjistí. Skutečné FP registru je nastavena na RSP + 16 \* toto číslo, což umožňuje posun od 0 do 240. To umožňuje odkazující FP reg doprostřed přidělení místního zásobníku pro dynamické zásobníku, umožňující lepší hustoty kódu prostřednictvím kratší pokyny (Další pokyny slouží formuláři znaménkem posunutí 8 bitů).

- **Pole kódy unwind**

   Toto je pole položek, který vysvětluje efekt prologu na stálé registry a RSP. V části na UNWIND_CODE pro význam jednotlivých položek. Pro účely zarovnání bude toto pole mít vždy sudý počet položek s poslední položka potenciálně nevyužité (v takovém případě bude pole jednoho déle, než je uvedeno podle počtu pole kódy unwind).

- **Adresa obslužné rutiny výjimek**

   To je ukazatel relativní bitové kopie do obslužné rutiny funkce pro konkrétní jazyk výjimce nebo ukončení (Pokud UNW_FLAG_CHAININFO příznak není zaškrtnut a příznaky UNW_FLAG_EHANDLER nebo UNW_FLAG_UHANDLER nastavený).

- **Data obslužné rutiny pro konkrétní jazyk**

   Jedná se o data obslužné rutiny výjimek specifické pro jazyk funkce. Formát dat je tento parametr zadán a zcela určeno obslužnou rutinu výjimky používá.

- **Zřetězené Unwind Info**

   Pokud je nastavený příznak UNW_FLAG_CHAININFO Struktura UNWIND_INFO končí řetězcem tři UWORD.  Tyto UWORD představují RUNTIME_FUNCTION informace o funkci zřetězené unwind.

## <a name="see-also"></a>Viz také

[Unwind data pro zpracování výjimek, podpora ladění](../build/unwind-data-for-exception-handling-debugger-support.md)