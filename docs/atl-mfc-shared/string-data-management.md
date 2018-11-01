---
title: Správa řetězcových dat
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: cbc48008cd7b30f1630fc4ec2c30214e3c448c27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595062"
---
# <a name="string-data-management"></a>Správa řetězcových dat

Visual C++ poskytuje několik způsobů, jak spravovat data řetězce:

- [Řetězec, manipulaci s](../c-runtime-library/string-manipulation-crt.md) pro práci se řetězců ve stylu C zakončený hodnotou null

- Funkce rozhraní Win32 API pro správu řetězce

- Třída knihovny MFC [cstringt – třída](../atl-mfc-shared/reference/cstringt-class.md), která poskytuje flexibilní, umožňující změnu velikosti řetězcových objektů

- Třída [cstringt – třída](../atl-mfc-shared/reference/cstringt-class.md), který poskytuje objekt knihovny MFC nezávislé na řetězec pomocí stejné funkce jako `CString`

Téměř všechny programy pracovat s řetězcovými daty. Knihovny MFC `CString` třídy je často nejlepší řešení pro zpracování flexibilní řetězce. Od verze 7.0, `CString` lze použít v aplikacích MFC nebo knihovny MFC nezávislé. Běhové knihovny a `CString` podporu řetězců obsahující vícebajtových znaků (rozsáhlé), stejně jako v kódování Unicode a MBCS programování.

Tento článek popisuje pro obecné účely služby, které poskytuje knihovna tříd související s zacházení s řetězci. V tomto článku probíraná témata zahrnují:

- [Kódování Unicode a MBCS poskytují přenositelnosti](#_core_unicode_and_mbcs_provide_portability)

- [CStrings a ukazatele const char](#_core_cstrings_and_const_char_pointers)

- [CString – počítání odkazů](#_core_cstring_reference_counting)

[Cstringt – třída](../atl-mfc-shared/reference/cstringt-class.md) třída poskytuje podporu pro manipulace s řetězci. Je určena k nahrazení a rozšíření funkcí obvykle poskytovaný balíček řetězec knihovny run-time C. `CString` Třída poskytuje členské funkce a operátory pro zjednodušené řetězec zpracování, podobné těm v Basic. Třída rovněž poskytuje konstruktory a operátory pro vytváření, přiřazování a porovnání `CString`s a standard C++ řetězec datové typy. Protože `CString` není odvozen od `CObject`, můžete použít `CString` objekty nezávisle na většinu z třídy knihovny MFC (Microsoft Foundation).

`CString` objekty podle "hodnota sémantiky." A `CString` objekt představuje jedinečnou hodnotu. Představte si, že `CString` jako vytvoření skutečného řetězce, nikoli jako ukazatel na řetězec.

A `CString` objekt představuje posloupnost proměnný počet znaků. `CString` objekty lze chápat jako pole znaků.

##  <a name="_core_unicode_and_mbcs_provide_portability"></a> Kódování Unicode a MBCS poskytují přenositelnosti

Knihovna MFC verze 3.0 nebo novější, MFC, včetně `CString`, je povolený pro kódování Unicode a vícebajtových znakových sad (MBCS). Tato podpora usnadňuje psaní přenosné aplikací, můžete tak vytvářet pro znaky sady Unicode nebo ANSI. K povolení této přenositelnosti každý znak v `CString` objekt je typu TCHAR, který je definován jako `wchar_t` definujete symbol _UNICODE při sestavování aplikace, nebo jako `char` Pokud tomu tak není. A `wchar_t` znak, který je 16 bitů široké. Znakové sady MBCS je povoleno, je-li sestavení s _MBCS symbol definovaný. Knihovna MFC sama využívá rozhraní symbol _MBCS (knihovnám NAFX) nebo symbol _UNICODE (knihovnám UAFX) definovaný.

> [!NOTE]
>  `CString` Příkladech v tomto a doprovodné články na řetězce literálu řetězce ve správném formátu pro přenositelnost Unicode, makro _T, což znamená řetězcového literálu na formuláři:

`L"literal string"`

> [!NOTE]
>  který kompilátor považuje za řetězec znaků Unicode. Například následující kód:

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
>  je přeložen jako řetězec znaků Unicode, pokud je definován _UNICODE nebo jako řetězec ANSI, pokud tomu tak není. Další informace najdete v článku [vícebajtové znakové sady (MBCS) Podpora kódování Unicode a](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

A `CString` objektu můžete uložit na INT_MAX (2 147 483 647) znaků. Tchar – datový typ se používá k získání nebo nastavení jednotlivých znaků uvnitř `CString` objektu. Na rozdíl od pole znaků `CString` třída má funkci přidělení paměti integrované. Díky tomu `CString` objekty automaticky růst podle potřeby (to znamená, není nutné se starat o růstu `CString` objekt přizpůsobena delší řetězce).

##  <a name="_core_cstrings_and_const_char_pointers"></a> CStrings a ukazatele const char

A `CString` objekt také může sloužit jako literál řetězce ve stylu jazyka C ( `PCXSTR`, což je stejná jako **const char** <strong>\*</strong> if není v kódování Unicode). [CSimpleStringT::operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) operátor převodu umožňuje `CString` objekty volně nahradí ukazatelů na znaky ve volání funkce. **CString (LPCWSTR** `pszSrc` **)** konstruktor umožňuje ukazatelů na znaky nahrazení `CString` objekty.

Bez pokusu o přeložení `CString` objekty. Pokud provedete dvě `CString` objekty obsahující `Chicago`, například znaky v `Chicago` jsou uložená na dvou místech. (Toto video asi platí pro budoucí verze knihovny MFC, takže by neměla na ní závisí.)

> [!NOTE]
>  Použití [CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) a [CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) členské funkce, když budete chtít přímý přístup k `CString` jako nekonstantním ukazatel na znak.

> [!NOTE]
>  Použití [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) a [CStringT::SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) členské funkce přidělení a nastavit BSTR objekty používané ve službě Automation (dříve označované jako automatizace OLE).

> [!NOTE]
>  Kde je to možné, přidělit `CString` objekty v rámci, nikoli na haldě. To šetří paměť a zjednodušuje předávání parametrů.

`CString` Třída není implementovaný jako kolekce třídu knihovny Microsoft Foundation Class, i když `CString` objekty mohou být uloženy jistě jako prvky v kolekci.

##  <a name="_core_cstring_reference_counting"></a> CString – počítání odkazů

Od verze knihovny MFC verze 4.0 když [cstringt – třída](../atl-mfc-shared/reference/cstringt-class.md) objekty jsou zkopírovány, MFC zvýší počet odkazů spíše než kopírování dat. Díky tomu předávání parametrů podle hodnoty a vrátí `CString` objekty podle hodnoty efektivnější. Tyto operace způsobovat kopírovací konstruktor, která se má volat, někdy více než jednou. Zvyšování počtu odkazů snižuje režii, že pro tyto běžné operace a pomocí provádí `CString` atraktivnější možnost.

Každá kopie je zničen, je snížen počet odkazů v původním objektu. Původní `CString` objektu není zničen, dokud jeho počet odkazů sníží na nulu.

Můžete použít `CString` členské funkce [CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) a [CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) můžete zakázat nebo Povolit počítání odkazů.

## <a name="see-also"></a>Viz také

[Obecná témata MFC](../mfc/general-mfc-topics.md)

