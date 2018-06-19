---
title: Typ data | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DATE
dev_langs:
- C++
helpviewer_keywords:
- Date data type, implementing
- Date data type
- DATE type
- Date data type, about Date data type
- MFC, date and time
- hour values representation
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5aafed046fa5724442e30014aa5634542de0f4aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358124"
---
# <a name="date-type"></a>DATE – typ
**Datum** typ je implementovaná pomocí číslo s plovoucí desetinnou čárkou 8 bajtů. Počet dnů jsou reprezentované pomocí přírůstcích celé číslo od 30 prosinec 1899, půlnoc jako čas nula. Hodnoty hodin jsou vyjádřené jako absolutní hodnotu čísla zlomkové části. Následující tabulka znázorňuje několik dat spolu s jejich **datum** číselný ekvivalent typu:  
  
|Datum a čas|Reprezentace|  
|-------------------|--------------------|  
|30 prosinec 1899, půlnoc|0.00|  
|1. ledna 1900 půlnoc|2.00|  
|4. ledna 1900 půlnoc|5.00|  
|4. ledna 1900, 6 hodin ráno|5.25|  
|4. ledna 1900 poledne|5.50|  
|4. ledna 1900 odp 9.|5.875|  
  
 **Datum** datum typ, a taky `COleDateTime` třídy, představuje data a časy jako classic číslo řádku. `COleDateTime` Třída obsahuje několik metod pro manipulaci s hodnoty data, včetně převodu do a z dalších běžných formátů data.  
  
 Při práci s těchto formátů data a času v automatizaci potřeba poznamenat následující body:  
  
-   Se data v místním čase; synchronizace je nutné ručně provést při práci s daty v různých časových pásmech.  
  
-   Typy data účtu není pro letní čas.  
  
-   Časová osa datum stane nespojitým pro hodnoty data menší než 0 (před 30 1899 prosince). Důvodem je, že část celé číslo hodnoty date je zpracovaná jako podepsané, zatímco zlomkové části považuje jako bez znaménka. Jinými slovy, celé číslo část hodnoty date může být kladná nebo záporná, zatímco zlomkové části hodnoty date je vždy přidán k datu celkové logické. Následující tabulka znázorňuje několik příkladů:  
  
|Datum a čas|Reprezentace|  
|-------------------|--------------------|  
|27 1899 prosinec, půlnoc|-3.00|  
|28 prosinec 1899 poledne|-2.50|  
|28 1899 prosinec, půlnoc|-2.00|  
|29 1899 prosinec, půlnoc|-1.00|  
|30 prosinec 1899, 6 hodin|-0.75|  
|30 prosinec 1899 poledne|-0.50|  
|30 prosinec 1899, 6 hodin ráno|-0.25|  
|30 prosinec 1899, půlnoc|0.00|  
|30 prosinec 1899, 6 hodin ráno|0.25|  
|30 prosinec 1899 poledne|0.50|  
|30 prosinec 1899, 6 hodin|0.75|  
|31. prosince 1899, půlnoc|1.00|  
|1. ledna 1900 půlnoc|2.00|  
|1. ledna 1900 poledne|2.50|  
|2. ledna 1900 půlnoc|3.00|  
  
> [!CAUTION]
>  Všimněte si, že protože 6:00:00 je vždy označena desetinnou hodnotu 0,25 bez ohledu na to, jestli je kladné celé číslo představující den (po 30 prosinec 1899) nebo záporné (před 30. prosince 1899), jednoduché plovoucí porovnání bodu by chybnou informací řazení všechny **datum** představující 6:00:00 v den starší než 12/30/1899 jako *později* než **datum** představující 7:00 AM v daný den stejné.  
  
 Další informace o problémy související s **datum** a `COleDateTime` typy naleznete v části [COleDateTime třída](../atl-mfc-shared/reference/coledatetime-class.md) a [datum a čas: Podpora automatizace](../atl-mfc-shared/date-and-time-automation-support.md).  
  
## <a name="see-also"></a>Viz také  
 [Datum a čas](../atl-mfc-shared/date-and-time.md)   
 [COleDateTime – třída](../atl-mfc-shared/reference/coledatetime-class.md)

