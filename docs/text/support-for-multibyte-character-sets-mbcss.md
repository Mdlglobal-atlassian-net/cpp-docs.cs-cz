---
title: "Podpora vícebajtových znakových sad (MBCS) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- multibyte characters [C++]
- MBCS [C++]
ms.assetid: b498733c-a1e1-45e3-8f26-d6da3cb5f2dd
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8c6c7bd1477f62e9c78b5e71dfe3723e804283d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="support-for-multibyte-character-sets-mbcss"></a>Podpora vícebajtových znakových sad (MBCS)
Vícebajtové znakové sady (MBCS) jsou starším přístupem k potřebě podporovat znakové sady, které nelze reprezentovat jediným bajtem, jako například japonštinu a čínštinu. Při novém vývoji by měla být pro všechny textové řetězce použita sada Unicode, snad kromě systémových řetězců, které koncový uživatel neuvidí. Sada MBCS je starou technologií a pro nový vývoj se nedoporučuje.  
  
 Nejběžnější MBCS implementace je dvoubajtové znakové sady (DBCS). Visual C++ v obecné a rozhraní MFC zejména je plně podporují pro znaky DBCS.  
  
 Ukázky naleznete v části soubory MFC zdrojového kódu.  
  
 Pro platformy použité na trzích, jejichž jazyky použít velké znakových sad je nejlepší alternativou k Unicode MBCS. MFC MBCS podporuje pomocí internationalizace datové typy a C běhové funkce. Stejné byste měli provést v kódu.  
  
 V části MBCS kódování znaků v bajtech 1 nebo 2. V 2bajtová znaků, první nebo úvodní bajt signalizuje, že ji a následující bajtů se interpretovat jako jeden znak. Prvním bajtem pochází z rozsahu kódů, které jsou vyhrazené pro použití jako úvodní bajty. Který rozsah bajtů může být úvodní bajty závisí na znaková stránka používá. Například japonské znaková stránka 932 používá rozsah 0x81 až 0x9F jako úvodní bajty, ale korejské znakové stránky 949 používá jiný rozsah.  
  
 Vezměte v úvahu všechny následující ve vašem MBCS programování.  
  
 Znaky znakové sady MBCS v prostředí  
 Znaky znakové sady MBCS se mohou objevit v řetězcích, jako jsou názvy souborů a adresářů.  
  
 Operace úprav  
 Operace v aplikacích MBCS úprav pracovat na znaků, ne v bajtech. Vsuvka by neměl rozdělit znak, šipka vpravo přesuňte jeden znak doprava a tak dále. **Odstranit** , měli byste odstranit znak; **Vrátit zpět** by znovu vložit.  
  
 Zpracování řetězce  
 V aplikaci, která používá MBCS představuje zpracování řetězce speciální problémy. Znaky obou šířek jsou kombinované ve jeden řetězec; proto musí nezapomeňte zkontrolovat úvodní bajty.  
  
 Podpora běhové knihovny  
 Běhové knihovny jazyka C a rozhraní MFC podporují jednobajtové, MBCS a Unicode programování. Jednobajtové řetězce jsou zpracovávány pomocí `str` řadu běhové funkce MBCS řetězce jsou zpracovávány pomocí odpovídajících `_mbs` funkce a řetězců v kódu Unicode jsou zpracovávány pomocí odpovídajících *serveru webového obsahu* funkce. Implementace funkce člena třídy knihovny MFC pomocí přenosné běhové funkce, které mapují správné okolností na normální `str` rodiny funkce, funkce znakové sady MBCS nebo funkce Unicode, jak je popsáno v "Přenositelnost MBCS/Unicode."  
  
 Přenositelnost MBCS/Unicode  
 Pomocí souboru Tchar.h záhlaví, můžete vytvořit jednobajtové, MBCS a Unicode aplikací ze stejného zdroje. Tchar.h definuje makra s *_tcs* , který mapování na `str`, `_mbs`, nebo *wcs* podle potřeby. Pokud chcete vytvořit MBCS, definujte symbol **_MBCS**. Chcete-li sestavit Unicode, definujte symbol **_UNICODE**. Ve výchozím nastavení **_MBCS** je definována pro aplikace MFC. Další informace najdete v tématu [mapování obecného textu v souboru Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
> [!NOTE]
>  Není definován chování, pokud obě definujete **_UNICODE** a **_MBCS**.  
  
 Soubory hlaviček Mbctype.h a Mbstring.h definovat MBCS specifické funkce a makra, které může být nutné v některých případech. Například `_ismbblead` zjistíte, jestli konkrétní bajtů v řetězci je úvodní bajt.  
  
 Pro mezinárodní přenositelnost kódu s vaším programem [Unicode](../text/support-for-unicode.md) nebo vícebajtových znakových sad (MBCS).  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Povolit MBCS v mém programu](../text/international-enabling.md)  
  
-   [Povolit kódování Unicode a MBCS v mém programu](../text/internationalization-strategies.md)  
  
-   [Použít k vytvoření mezinárodního programu MBCS](../text/mbcs-programming-tips.md)  
  
-   [Zobrazit souhrn programování znakové sady MBCS](../text/mbcs-programming-tips.md)  
  
-   [Další informace o mapování obecného textu pro přenositelnost šířky bajtu](../text/generic-text-mappings-in-tchar-h.md)  
  
## <a name="see-also"></a>Viz také  
 [Text a řetězce](../text/text-and-strings-in-visual-cpp.md)   
 [Podpora znakové sady MBCS v jazyku Visual C++](../text/mbcs-support-in-visual-cpp.md)