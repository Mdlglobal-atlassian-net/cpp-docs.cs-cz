---
title: 'TN059: Použití převodních maker MBCS-Unicode prostředí MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- MFCANS32.DLL
- Unicode [MFC], conversion macros
- Unicode [MFC], OLE interfaces
- conversion macros [MFC]
- converting Unicode
- MBCS [MFC], conversion macros
- macros [MFC], MBCS conversion macros
- TN059
ms.assetid: a2aab748-94d0-4e2f-8447-3bd07112a705
ms.openlocfilehash: 657381d8247aef14b2c725996dfeb11d0e0535fe
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749441"
---
# <a name="tn059-using-mfc-mbcsunicode-conversion-macros"></a>TN059: Použití převodních maker MBCS/Unicode prostředí MFC

> [!NOTE]
> Následující technická poznámka nebyla aktualizována od doby, kdy byla poprvé zahrnuta do online dokumentace. V důsledku toho mohou být některé postupy a témata zastaralé nebo nesprávné. Chcete-li získat nejnovější informace, doporučujeme vyhledat téma zájmu v online indexu dokumentace.

Tato poznámka popisuje použití maker pro převod MBCS/Unicode, které jsou definovány v AFXPRIV. H. Tato makra jsou nejužitečnější, pokud vaše aplikace řeší přímo rozhraní OLE API nebo z nějakého důvodu často potřebuje převést mezi Unicode a MBCS.

## <a name="overview"></a>Přehled

V knihovně MFC 3.x byla použita speciální knihovna DLL (MFCANS32. DLL) pro automatický převod mezi unicode a mbcs při volání rozhraní OLE. Tato knihovna DLL byla téměř průhledná vrstva, která umožňovala zápis aplikací OLE, jako by rozhraní OLE API a rozhraní byla MBCS, i když jsou vždy Unicode (s výjimkou macintosh). Zatímco tato vrstva byla pohodlná a umožnila aplikacím rychle přenést z Win16 na Win32 (MFC, Microsoft Word, Microsoft Excel a VBA, jsou jen některé z aplikací společnosti Microsoft, které používaly tuto technologii), měly někdy významný výkon. Z tohoto důvodu knihovna MFC 4.x nepoužívá tuto knihovnu DLL a místo toho hovoří přímo s rozhraními UNICODE OLE. Chcete-li to provést, mfc musí převést na Unicode mbcs při volání rozhraní OLE a často potřebuje převést na MBCS z Unicode při implementaci rozhraní OLE. Aby bylo možné tento účel a snadno zpracovat, byla vytvořena řada maker, která tento převod usnadňují.

Jednou z největších překážek vytvoření takové sady maker je přidělení paměti. Vzhledem k tomu, že řetězce nelze převést na místě, musí být přidělena nová paměť pro uložení převedených výsledků. To by mohlo být provedeno s kódem podobným následujícímu:

```
// we want to convert an MBCS string in lpszA
int nLen = MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    NULL,
    NULL);

LPWSTR lpszW = new WCHAR[nLen];
MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    lpszW,
    nLen);

// use it to call OLE here
pI->SomeFunctionThatNeedsUnicode(lpszW);

// free the string
delete[] lpszW;
```

Tento přístup jako řada problémů. Hlavním problémem je, že je hodně kódu pro psaní, testování a ladění. Něco, co bylo jednoduché volání funkce, je nyní mnohem složitější. Kromě toho je významné režie runtime v tom. Paměť musí být přidělena na haldě a uvolněna při každém převodu. Nakonec výše uvedený kód bude `#ifdefs` muset mít vhodné přidány pro sestavení Unicode a Macintosh (které nevyžadují tento převod uskutečnit).

Řešení, které jsme přišli s je vytvořit některé makra, které 1) maskovat rozdíl mezi různými platformami a 2) použít efektivní schéma přidělení paměti, a 3) jsou snadno vložit do existujícího zdrojového kódu. Zde je příklad jedné z definic:

```
#define A2W(lpa) (\
((LPCSTR)lpa == NULL) NULL : (\
    _convert = (strnlen(lpa)+1),\
    AfxA2WHelper((LPWSTR) alloca(_convert*2),
    lpa,
    _convert)\)\)
```

Použití tohoto makra namísto výše uvedeného kódu a věci jsou mnohem jednodušší:

```
// use it to call OLE here
USES_CONVERSION;
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));
```

Existují další volání, kde je nutný převod, ale použití maker je jednoduché a efektivní.

Implementace každého makra používá funkci _alloca() k přidělení paměti ze zásobníku namísto haldy. Přidělování paměti ze zásobníku je mnohem rychlejší než přidělování paměti na haldě a paměť je automaticky uvolněna při ukončení funkce. Kromě toho se makra vyhýbají volání `MultiByteToWideChar` (nebo `WideCharToMultiByte`) více než jednomu času. To se provádí přidělením trochu více paměti, než je nutné. Víme, že MBC převede na maximálně jeden **WCHAR** a že pro každý **WCHAR** budeme mít maximálně dva bajty MBC. Přidělením o něco více, než je nutné, ale vždy dost pro zpracování převodu druhé volání druhé volání funkce převodu je zabráněno. Volání pomocné funkce `AfxA2Whelper` snižuje počet argument pushy, které musí být provedeny za účelem provedení převodu `MultiByteToWideChar` (to má za následek menší kód, než kdyby je volána přímo).

Chcete-li, aby makra měla prostor pro uložení dočasné délky, je nutné deklarovat místní proměnnou nazvanou _convert, která to provádí v každé funkci, která používá makra převodu. To se provádí vyvoláním USES_CONVERSION makro, jak je vidět výše v příkladu.

Existují obecná makra převodu a makra specifická pro OLE. Tyto dvě různé sady maker jsou popsány níže. Všechna makra jsou umístěna v AFXPRIV. H.

## <a name="generic-conversion-macros"></a>Obecná makra převodu

Obecná makra převodu tvoří základní mechanismus. Příklad maker a implementace zobrazená v předchozí části A2W je jedním z takových "obecných" maker. Nesouvisí konkrétně s OLE. Sada obecných maker je uvedena níže:

```
A2CW      (LPCSTR) -> (LPCWSTR)
A2W      (LPCSTR) -> (LPWSTR)
W2CA      (LPCWSTR) -> (LPCSTR)
W2A      (LPCWSTR) -> (LPSTR)
```

Kromě převodu textu existují také makra a pomocné `DEVMODE` `BSTR`funkce pro převod `TEXTMETRIC`řetězců , , a OLE. Tato makra jsou nad rámec této diskuse – viz AFXPRIV. H pro další informace o těchto maker.

## <a name="ole-conversion-macros"></a>Makra převodu OLE

Makra převodu OLE jsou navrženy speciálně pro zpracování funkcí, které očekávají znaky **OLESTR.** Pokud zkontrolujete hlavičky OLE, zobrazí se mnoho odkazů na **LPCOLESTR** a **OLECHAR**. Tyto typy se používají k odkazování na typ znaků používaných v rozhraní OLE způsobem, který není specifický pro platformu. **OLECHAR** mapuje **char** v Win16 a Macintosh platformy a **WCHAR** v Win32.

Aby byl počet **direktiv #ifdef** v kódu knihovny MFC na minimum, máme podobné makro pro každý převod, který se týká, pokud jsou zapojeny řetězce OLE. Nejčastěji se používají následující makra:

```
T2COLE   (LPCTSTR) -> (LPCOLESTR)
T2OLE   (LPCTSTR) -> (LPOLESTR)
OLE2CT   (LPCOLESTR) -> (LPCTSTR)
OLE2T   (LPCOLESTR) -> (LPCSTR)
```

Opět existují podobné makra pro práci TEXTMETRIC, DEVMODE, BSTR a OLE přidělené řetězce. Viz AFXPRIV. H pro více informací.

## <a name="other-considerations"></a>Ostatní úvahy

Nepoužívejte makra v těsné smyčce. Například nechcete psát následující druh kódu:

```cpp
void BadIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, T2COLE(lpsz));

}
```

Výše uvedený kód může mít za následek přidělení megabajtů paměti v zásobníku `lpsz` v závislosti na tom, jaký je obsah řetězce! Také trvá nějakou dobu převést řetězec pro každou iteraci smyčky. Místo toho přesuňte tyto konstantní převody mimo smyčku:

```cpp
void MuchBetterIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    LPCOLESTR lpszT = T2COLE(lpsz);

    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, lpszT);

}
```

Pokud řetězec není konstantní, pak zapouzdřte volání metody do funkce. To umožní vyrovnávací paměti převodu uvolnit pokaždé. Příklad:

```cpp
void CallSomeMethod(int ii, LPCTSTR lpsz)
{
    USES_CONVERSION;
    pI->SomeMethod(ii, T2COLE(lpsz));

}

void MuchBetterIterateCode2(LPCTSTR* lpszArray)
{
    for (int ii = 0; ii <10000; ii++)
    CallSomeMethod(ii, lpszArray[ii]);

}
```

Nikdy vrátit výsledek jednoho z maker, pokud vrácená hodnota znamená vytvoření kopie dat před vrácení. Například tento kód je chybný:

```
LPTSTR BadConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // bad! returning alloca memory
}
```

Výše uvedený kód může být opraven změnou vrácené hodnoty na něco, co zkopíruje hodnotu:

```
CString BetterConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // CString makes copy
}
```

Makra se snadno používají a snadno se vkládají do kódu, ale jak můžete zjistit z výše uvedených upozornění, musíte být opatrní při jejich použití.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
