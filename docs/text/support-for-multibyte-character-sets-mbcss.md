---
title: Podpora vícebajtových znakových sad (MBCS)
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- multibyte characters [C++]
- MBCS [C++]
ms.assetid: b498733c-a1e1-45e3-8f26-d6da3cb5f2dd
ms.openlocfilehash: 0b43168ec4331e99dea7e939b097674cc880804e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375767"
---
# <a name="support-for-multibyte-character-sets-mbcss"></a>Podpora vícebajtových znakových sad (MBCS)

Vícebajtové znakové sady (MBCS) jsou starším přístupem k potřebě podporovat znakové sady, které nelze reprezentovat jediným bajtem, jako například japonštinu a čínštinu. Při novém vývoji by měla být pro všechny textové řetězce použita sada Unicode, snad kromě systémových řetězců, které koncový uživatel neuvidí. Sada MBCS je starou technologií a pro nový vývoj se nedoporučuje.

Nejběžnější implementací mbcs je dvoubajtové znakové sady (DBCS). Visual C++ obecně a knihovny MFC zejména je plně povolena pro DBCS.

Ukázky naleznete v souborech zdrojového kódu knihovny MFC.

Pro platformy používané na trzích, jejichž jazyky používají velké znakové sady, je nejlepší alternativou k Unicode MBCS. Knihovna MFC podporuje knihovnu MBCS pomocí mezinárodněelných datových typů a funkcí c run-time. Měli byste udělat totéž ve vašem kódu.

V části MBCS jsou znaky kódovány v 1 nebo 2 bajty. V dvoubajtových znacích první nebo hlavní bajt signalizuje, že jej i následující bajt mají být interpretovány jako jeden znak. První bajt pochází z rozsahu kódů vyhrazených pro použití jako úvodní bajty. Rozsahy bajtů mohou být úvodní bajty závisí na znakové stránce v použití. Například japonská znaková stránka 932 používá rozsah 0x81 až 0x9F jako úvodní bajty, ale korejská znaková stránka 949 používá jiný rozsah.

Zvažte všechny následující v programování MBCS.

Znaky mbcs v prostředí mbcs znaky se mohou objevit v řetězcích, jako jsou názvy souborů a adresářů.

### <a name="editing-operations"></a>Úpravy operací

Operace úprav v aplikacích MBCS by měly pracovat se znaky, nikoli s bajty. Stříška by neměla rozdělit znak, **šipka vpravo** by se měla posunout o jeden znak doprava a tak dále. **Odstranit** by měl odstranit znak; **Zpět** by měl znovu vložit.

### <a name="string-handling"></a>Manipulace s řetězci

V aplikaci, která používá mbcs, zpracování řetězců představuje zvláštní problémy. Znaky obou šířek jsou smíchány v jednom řetězci; proto je třeba zkontrolovat úvodní bajty.

### <a name="run-time-library-support"></a>Podpora knihovny run-time

Knihovna C run-time a knihovna MFC podporují jednobajtové, mbcs a unicode programování. Jednobajtové řetězce jsou zpracovávány `str` s rodinou funkcí za běhu, řetězce MBCS jsou zpracovávány s odpovídajícími `_mbs` `wcs` funkcemi a řetězce Unicode jsou zpracovávány s odpovídajícími funkcemi. Implementace členských funkcí třídy knihovny MFC používají přenosné funkce za běhu, `str` které za správných okolností mapují na normální řadu funkcí, funkce MBCS nebo funkce Unicode, jak je popsáno v "Přenositelnost MBCS/Unicode".

### <a name="mbcsunicode-portability"></a>Přenositelnost mbcs/unicode

Pomocí souboru záhlaví tchar.h můžete vytvářet jednobajtové aplikace, mbcs a unicode ze stejných zdrojů. Soubor Tchar.h definuje makra s předponou `wcs` *_tcs* , která jsou podle potřeby mapována na `str` `_mbs`, nebo funkce. Chcete-li vytvořit sadu MBCS, definujte symbol `_MBCS`. Chcete-li vytvořit unicode, definujte symbol `_UNICODE`. Ve výchozím `_UNICODE` nastavení je definována pro aplikace knihovny MFC. Další informace naleznete [v tématu Mapování obecného textu v souboru tchar.h](../text/generic-text-mappings-in-tchar-h.md).

> [!NOTE]
> Chování není definováno, `_UNICODE` pokud `_MBCS`definujete obě a .

Soubory hlaviček Mbctype.h a Mbstring.h definují funkce a makra specifické pro mbcs, které můžete v některých případech potřebovat. Například `_ismbblead` vás řekne, zda konkrétní bajt v řetězci je zájemce bajt.

Pro mezinárodní přenositelnost kódujte program pomocí znakových sad [Unicode](../text/support-for-unicode.md) nebo vícebajtových znaků (MBCS).

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Povolení mbcs v programu](../text/international-enabling.md)

- [Povolení kódování Unicode i znakové paměti MBCS v programu](../text/internationalization-strategies.md)

- [Vytvoření internacionalizovaného programu pomocí mbcs](../text/mbcs-programming-tips.md)

- [Zobrazit souhrn programování mbcs](../text/mbcs-programming-tips.md)

- [Informace o mapování obecného textu pro přenositelnost šířky bajtů](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Viz také

[Text a řetězce](../text/text-and-strings-in-visual-cpp.md)<br/>
[Podpora znakové sady MBCS v jazyku Visual C++](../text/mbcs-support-in-visual-cpp.md)
