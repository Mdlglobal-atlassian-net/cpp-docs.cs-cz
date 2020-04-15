---
title: Správa řetězcových dat
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: 7f92b38ac659faef2dd9319b2f204ba837f0d473
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317454"
---
# <a name="string-data-management"></a>Správa řetězcových dat

Visual C++ poskytuje několik způsobů správy řetězcových dat:

- [Manipulace s řetězci](../c-runtime-library/string-manipulation-crt.md) pro práci s řetězci ukončenými nula ve stylu C

- Funkce rozhraní API win32 pro správu řetězců

- [Třída CStringT třídy](../atl-mfc-shared/reference/cstringt-class.md)knihovny MFC , která poskytuje flexibilní objekty s nastavitelnou platností

- [Třída CStringT Class](../atl-mfc-shared/reference/cstringt-class.md), která poskytuje řetězec nezávislý na knihovně MFC se stejnou funkcí jako`CString`

Téměř všechny programy pracují s řetězcovými daty. Třída knihovny `CString` MFC je často nejlepším řešením pro flexibilní zpracování řetězců. Počínaje verzí 7.0 `CString` lze použít v programech nezávislých na knihovně MFC nebo MFC. Knihovna za běhu `CString` i řetězce podpory obsahující vícebajtové (široké) znaky, jako v programu Unicode nebo MBCS.

Tento článek popisuje služby pro obecné účely, které knihovna tříd poskytuje v souvislosti s manipulací s řetězci. Témata uvedená v tomto článku zahrnují:

- [Unicode a MBCS poskytují přenositelnost](#_core_unicode_and_mbcs_provide_portability)

- [CStrings a const char ukazatele](#_core_cstrings_and_const_char_pointers)

- [CString Reference Counting](#_core_cstring_reference_counting)

Třída [CStringT](../atl-mfc-shared/reference/cstringt-class.md) poskytuje podporu pro manipulaci s řetězci. Je určena k nahrazení a rozšíření funkce obvykle poskytované c run-time knihovny řetězec balíčku. Třída `CString` poskytuje členské funkce a operátory pro zjednodušené zpracování řetězců, podobně jako v basic. Třída také poskytuje konstruktory a operátory pro vytváření, `CString`přiřazování a porovnávání s a standardní c++ řetězce datových typů. Protože `CString` není odvozen `CObject`od , `CString` můžete použít objekty nezávisle na většině Knihovny tříd Microsoft Foundation (MFC).

`CString`objekty následují za "hodnotou sémantiky". Objekt `CString` představuje jedinečnou hodnotu. Představte `CString` si jako skutečný řetězec, nikoli jako ukazatel na řetězec.

Objekt `CString` představuje posloupnost proměnného počtu znaků. `CString`objekty lze považovat za pole znaků.

## <a name="unicode-and-mbcs-provide-portability"></a><a name="_core_unicode_and_mbcs_provide_portability"></a>Unicode a MBCS poskytují přenositelnost

S knihovnou MFC verze 3.0 `CString`a novější mfc, včetně , je povolena pro unicode a vícebajtové znakové sady (MBCS). Tato podpora usnadňuje psaní přenosných aplikací, které můžete vytvářet pro znaky Unicode nebo ANSI. Chcete-li povolit tuto přenositelnost, každý znak v objektu `CString` je typu TCHAR, který je definován jako `wchar_t` pokud definujete symbol _UNICODE při vytváření aplikace, nebo jako `char` kdyby ne. Znak `wchar_t` je 16 bitů široký. MBCS je povolena, pokud vytvoříte se symbolem _MBCS definován. Knihovna MFC sama o sobě je vytvořena buď se symbolem _MBCS (pro knihovny NAFX), nebo _UNICODE symbolem (pro knihovny UAFX).

> [!NOTE]
> Příklady `CString` v tomto a doprovodné články o řetězecích ukazují literálové řetězce správně formátované pro přenositelnost Unicode pomocí _T makru, které převádí literálový řetězec do formuláře:

`L"literal string"`

> [!NOTE]
> který kompilátor považuje za řetězec Unicode. Například následující kód:

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
> je přeložen jako řetězec Unicode, pokud je definován _UNICODE nebo jako řetězec ANSI, pokud ne. Další informace naleznete v článku [Podpora znakové sady Unicode a vícebajtové znakové sady (MBCS).](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

Objekt `CString` může uložit až INT_MAX (2 147 483 647) znaků. Datový typ TCHAR se používá k získání `CString` nebo nastavení jednotlivých znaků uvnitř objektu. Na rozdíl od `CString` polí znaků má třída schopnost integrovaného přidělení paměti. To `CString` umožňuje objektům automaticky růst podle potřeby (to znamená, `CString` že se nemusíte starat o rozšíření objektu tak, aby se vešel do delších řetězců).

## <a name="cstrings-and-const-char-pointers"></a><a name="_core_cstrings_and_const_char_pointers"></a>CStrings a const char ukazatele

Objekt `CString` také může fungovat jako řetězec v literálu stylu C `PCXSTR`(a , který je stejný jako **const char,** <strong>\*</strong> pokud není v rámci Unicode). Operátor převodu [CSimpleStringT::operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) umožňuje `CString` objektům volně nahrazovat ukazatele znaků ve volání funkce. **Konstruktor CString( LPCWSTR** `pszSrc` **)** umožňuje nahradit `CString` objekty ukazateli znaků.

Není proveden žádný `CString` pokus o přeložení objektů. Pokud vytvoříte `CString` dva `Chicago`objekty obsahující , `Chicago` například znaky v jsou uloženy na dvou místech. (To nemusí být pravda, budoucí verze knihovny MFC, takže byste neměli záviset na něm.)

> [!NOTE]
> Použijte [cSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) a [CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) členské funkce, když `CString` potřebujete přímý přístup jako nekonstantní ukazatel na znak.

> [!NOTE]
> Pomocí členských funkcí [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) a [CStringT::SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) přidělujte a nastavujte objekty BSTR používané v automatizaci (dříve označované jako automatizace OLE).

> [!NOTE]
> Pokud je `CString` to možné, přidělte objekty na rámečku, nikoli na haldě. To šetří paměť a zjednodušuje předávání parametrů.

Třída `CString` není implementována jako třída kolekce Knihovny tříd microsoft foundation, i když `CString` objekty mohou být jistě uloženy jako prvky v kolekcích.

## <a name="cstring-reference-counting"></a><a name="_core_cstring_reference_counting"></a>CString Reference Counting

Od knihovny MFC verze 4.0 při kopírování objektů [třídy CStringT](../atl-mfc-shared/reference/cstringt-class.md) mfc přerůstá počet odkazů spíše než kopírování dat. Díky předávání parametrů podle hodnoty `CString` a vrácení objektů podle hodnoty efektivnější. Tyto operace způsobit kopie konstruktoru, které mají být volány, někdy více než jednou. Zvýšení počet odkazů snižuje tuto režii pro `CString` tyto běžné operace a umožňuje použití atraktivnější možnost.

Jako každá kopie je zničena, počet odkazů v původním objektu je snížena. Původní `CString` objekt není zničen, dokud jeho počet odkazů je snížena na nulu.

`CString` Pomocí členských funkcí [CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) a [CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) můžete zakázat nebo povolit počítání odkazů.

## <a name="see-also"></a>Viz také

[Obecná témata MFC](../mfc/general-mfc-topics.md)
