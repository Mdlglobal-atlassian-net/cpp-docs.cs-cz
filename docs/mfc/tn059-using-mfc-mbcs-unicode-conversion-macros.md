---
title: 'TN059: Použití převodních maker MBCS-Unicode MFC | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.mbcs
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 232a590c7e0d2a494b447a260ab4920a148c2e0d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443914"
---
# <a name="tn059-using-mfc-mbcsunicode-conversion-macros"></a>TN059: Použití převodních maker MBCS/Unicode prostředí MFC

> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato poznámka popisuje způsob použití makra převodu znakové sady MBCS/Unicode, které jsou definovány v AFXPRIV. H. Tato makra jsou nejužitečnější tehdy, pokud svých obchodů používáte aplikaci přímo s rozhraním OLE API nebo z nějakého důvodu, často potřebuje pro převod mezi kódování Unicode a MBCS.

## <a name="overview"></a>Přehled

V prostředí MFC 3.x, speciální knihovny DLL se používá (MFCANS32. Knihovny DLL) mají automaticky převádět mezi kódování Unicode a MBCS, když byly volány rozhraní OLE. Tato knihovna DLL byla téměř transparentní vrstvu, která povolené OLE – aplikace má být zapsán jako šlo OLE API a rozhraní MBCS, i když jsou vždy kódování Unicode (s výjimkou Macintosh). Zatímco tato vrstva pohodlný a povolená aplikace rychle přenést z Win16 na Win32 (MFC, aplikace Microsoft Word, Microsoft Excelu a VBA, jsou jen některé z aplikací Microsoftu, které tuto technologii využívala), bylo v některých případech významné výkonnostní přístupů. Z tohoto důvodu MFC 4.x nepoužívá tuto knihovnu DLL a místo toho komunikuje přímo na rozhraní OLE kódování Unicode. K tomuto účelu MFC je potřeba převést do kódování Unicode do znakové sady MBCS při volání do rozhraní OLE a často je potřeba převést do znakové sady MBCS z kódování Unicode při implementaci rozhraní OLE. Pokud chcete se o to postarají efektivní a snadno, počtu maker byly vytvořeny pro usnadnění tohoto převodu.

Jednou z největších mezní hodnoty vytvoření sady makra je přidělení paměti. Protože řetězce nelze převést na místě, musí být přiděleny nové paměti k ukládání převedený výsledků. To může jsme udělali s kódem podobný následujícímu:

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

Tento přístup jako různé problémy. Hlavní problém je, že je velké množství kódu pro zápis, testování a ladění. Něco, co bylo volání jednoduchou funkci, je teď mnohem složitější. Režie při tom je navíc významné modul runtime. Paměť musí být přidělený k haldě a uvolnění pokaždé, když se provádí převod. Nakonec se výše uvedený kód byste potřebovali mít odpovídající `#ifdefs` přidání pro kódování Unicode a Macintosh sestavení (které nevyžadují tento převod uskutečnit).

Řešení, které jsme přišli s je vytvořit některé makra, které (1) maska rozdíl mezi různými platformami a (2) použití režimu přidělení paměti efektivní a 3) jsou snadno vkládat do existující zdrojový kód. Tady je příklad jednoho z definice:

```
#define A2W(lpa) (\
((LPCSTR)lpa == NULL) NULL : (\
    _convert = (strnlen(lpa)+1),\
    AfxA2WHelper((LPWSTR) alloca(_convert*2),
    lpa,
    _convert)\)\)
```

Pomocí tohoto makra namísto výše uvedený kód a co jsou mnohem jednodušší:

```
// use it to call OLE here
USES_CONVERSION;
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));
```

Existují další volání, kde převodu je nezbytné, ale pomocí makra je snadné a efektivní.

Provádění jednotlivých – makro používá funkci _alloca() je přidělit paměť ze zásobníku namísto haldy. Přidělování paměti ze zásobníku je mnohem rychlejší než přidělování paměti v haldě a paměť je automaticky uvolněn, když funkce skončí. Kromě toho se vyhnout volání makra `MultiByteToWideChar` (nebo `WideCharToMultiByte`) více než jednou. To se provádí přidělením trochu více paměti, než je nezbytné. Víme, že MBC převede na nejvýše jedna **WCHAR** a že pro každou **WCHAR** budeme mít maximálně dva bajty MBC. Přidělením trochu více než nezbytné, ale vždy dostatečně ke zpracování převodu druhé volání za druhé volání funkce pro převod je vyloučeno. Volání funkce pomocné rutiny `AfxA2Whelper` snižuje počet argumentů nabízených oznámení, které je třeba provést, aby bylo možné provést převod (výsledkem je menší kód, než pokud volána `MultiByteToWideChar` přímo).

Aby maker na místa k uložení dočasné délku, je potřeba deklarovat lokální proměnnou s názvem _převést, který to dělá v každé funkci, která používá makra převodů. To se provádí vyvoláním makra USES_CONVERSION, jak je znázorněno v příkladu výše.

Existují obecný převodních maker a konkrétní makra OLE. Tyto dvě různé – makro sady jsou popsány níže. Všechna makra jsou umístěny v AFXPRIV. H.

## <a name="generic-conversion-macros"></a>Obecný převodních maker

Obecný převodních maker tvoří základní mechanismus. Příklad makra a implementace uvedené v předchozí části, A2W, je jedno "generic" makro. Nesouvisí se OLE zvlášť. Sada obecné makra jsou uvedeny níže:

```
A2CW      (LPCSTR) -> (LPCWSTR)
A2W      (LPCSTR) -> (LPWSTR)
W2CA      (LPCWSTR) -> (LPCSTR)
W2A      (LPCWSTR) -> (LPSTR)
```

Kromě provádění text převody, jsou k dispozici také makra a pomocné funkce pro převod `TEXTMETRIC`, `DEVMODE`, `BSTR`a OLE přidělené řetězce. Tato makra jsou nad rámec této diskuse – AFXPRIV odkazovat. Další informace o těchto maker H.

## <a name="ole-conversion-macros"></a>Makra převodů OLE

Makra převodů OLE jsou navrženy speciálně pro zpracování funkcí, které očekávají **OLESTR** znaků. Když si zblízka záhlaví OLE, zobrazí se mnoho odkazů na **LPCOLESTR** a **OLECHAR**. Tyto typy se používají k odkazování na typ znaky použité v rozhraní OLE, které nejsou specifické pro platformu způsobem. **OLECHAR** mapuje **char** Win16 a Macintosh platforem a **WCHAR** v systému Win32.

Aby bylo možné zachovat počet **#ifdef** direktivy v MFC kód na minimum máme podobné – makro pro každý převod, kde se podílejí řetězce OLE. Nejčastěji se používají následující makra:

```
T2COLE   (LPCTSTR) -> (LPCOLESTR)
T2OLE   (LPCTSTR) -> (LPOLESTR)
OLE2CT   (LPCOLESTR) -> (LPCTSTR)
OLE2T   (LPCOLESTR) -> (LPCSTR)
```

Znovu jsou makra podobná TEXTMETRIC, DEVMODE, BSTR a OLE přidělené řetězce. Odkazovat na AFXPRIV. H Další informace.

## <a name="other-considerations"></a>Ostatní úvahy

Nepoužívejte makra v těsné smyčce. Například nechcete napsat následující druh kódu:

```
void BadIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, T2COLE(lpsz));

}
```

Výše uvedený kód by mohlo způsobit přidělování megabajtů paměti na zásobníku v závislosti na tom, jaký obsah řetězce `lpsz` je! Přijímá také čas pro převod řetězce pro každou iteraci smyčky. Místo toho přesuňte takové konstantním převodům smyčka:

```
void MuchBetterIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    LPCOLESTR lpszT = T2COLE(lpsz);

    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, lpszT);

}
```

Pokud řetězec není konstantní, pak zapouzdření volání metody na funkci. To vám umožní převod vyrovnávací paměti k uvolnění pokaždé, když. Příklad:

```
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

Nikdy nevracet výsledkem jednoho z makra, pokud vrácená hodnota znamená, že zkopíruje data před vrácení. Například tento kód je chybný:

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

Výše uvedený kód může napravit změnou návratovou hodnotu na něco, který kopíruje hodnotu:

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

Makra jsou snadno použitelné a snadno vkládat do kódu, ale jak vidíte z výše uvedených upozornění, musíte být opatrní při jejich používání.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

