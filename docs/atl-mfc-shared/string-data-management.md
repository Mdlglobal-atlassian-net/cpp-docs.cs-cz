---
title: "Řetězec dat správy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords: Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad7a17b1b34375fcb45019bcaf8878757288a290
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="string-data-management"></a>Správa dat řetězců
Visual C++ poskytuje několik způsobů, jak spravovat data řetězec:  
  
-   [Manipulace s řetězci](../c-runtime-library/string-manipulation-crt.md) pro práci s řetězce ukončené hodnotou null stylu jazyka C  
  
-   Funkce rozhraní Win32 API pro správu řetězce  
  
-   Třída knihovny MFC [CStringT třída](../atl-mfc-shared/reference/cstringt-class.md), která poskytuje flexibilní, s možností změny velikosti řetězcových objektů  
  
-   Třída [CStringT třída](../atl-mfc-shared/reference/cstringt-class.md), který poskytuje stejné funkce jako objekt řetězci nezávislé na MFC`CString`  
  
 Téměř všechny programy pracovat s řetězcovými daty. Knihovny MFC `CString` třída je často nejlepším řešením pro zpracování flexibilní řetězce. Počínaje verzí 7.0, `CString` lze použít v aplikacích MFC nebo MFC nezávislé. Běhové knihovny a `CString` podporují řetězce obsahující vícebajtových znaků (wide), jako kódování Unicode a MBCS programování.  
  
 Tento článek popisuje obecný služby, které poskytuje knihovna tříd souvisejících s zacházení s řetězci. Témata popsaná v tomto článku:  
  
-   [Kódování Unicode a MBCS poskytují přenositelnost](#_core_unicode_and_mbcs_provide_portability)  
  
-   [CStrings a const char ukazatele](#_core_cstrings_and_const_char_pointers)  
  
-   [CString při počítání referencí](#_core_cstring_reference_counting)  
  
 [CStringT třída](../atl-mfc-shared/reference/cstringt-class.md) třída poskytuje podporu pro manipulace s řetězci. Je určena k nahrazení a rozšířit funkce obvykle poskytované balíček řetězec běhové knihovny jazyka C. `CString` Třída poskytuje členských funkcí a operátory pro zjednodušené řetězec zpracování, podobné těm, které jsou součástí Basic. Třída také poskytuje konstruktory a operátory pro vytváření, přiřazení a porovnání **CStrings** a datové typy řetězec standardní C++. Protože `CString` není odvozen od `CObject`, můžete použít `CString` objekty nezávisle na většinu z Microsoft Foundation Class Library (MFC).  
  
 `CString`objekty podle "hodnota sémantiku." A `CString` objekt představuje jedinečnou hodnotu. Představte si, že `CString` jako řetězec skutečného, ne jako ukazatel na řetězec.  
  
 A `CString` objekt představuje posloupnost proměnný počet znaků. `CString`objekty lze považovat za pole znaků.  
  
##  <a name="_core_unicode_and_mbcs_provide_portability"></a>Kódování Unicode a MBCS poskytují přenositelnost  
 S MFC verze 3.0 nebo novější, MFC, včetně `CString`, je povolený pro kódování Unicode a vícebajtových znakových sad (MBCS). Tato podpora usnadňuje psaní aplikací přenosné, že můžete vytvořit pro znaky Unicode nebo ANSI. Chcete-li povolit tuto přenositelnost každý znak v `CString` objekt je typu **Tchar –**, který je definován jako `wchar_t` Pokud definujete symbol **_UNICODE** při sestavování vaší aplikace, nebo jako `char` není-li. A `wchar_t` znak je široké 16 bitů. Znakové sady MBCS je povoleno, pokud vytvoříte symbolem **_MBCS** definované. MFC samotné sestaveno s buď **_MBCS** symbol (pro knihovny NAFX) nebo **_UNICODE** symbol (pro knihovny UAFX) definované.  
  
> [!NOTE]
>  `CString` Příklady v tomto a doplňujícími články na řetězce zobrazení literálu řetězce ve správném formátu pro přenositelnosti znakové sady Unicode, pomocí **_T** makro, který překládá řetězcového literálu do formuláře:  
  
 `L"literal string"`  
  
> [!NOTE]
>  které kompilátor zpracovává jako řetězec znaků Unicode. Například následující kód:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]  
  
> [!NOTE]
>  je přeložená jako řetězec znaků Unicode, pokud **_UNICODE** je definována nebo jako ANSI řetězci, pokud není. Další informace najdete v článku [Podpora vícebajtových znakovou sadu (MBCS) kódování Unicode a](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).  
  
 A `CString` objekt může ukládat až **INT_MAX** (2 147 483 647) znaků. **Tchar –** datový typ se používá k získání nebo nastavení jednotlivých znaky uvnitř `CString` objektu. Na rozdíl od znaková pole `CString` třída má funkce přidělení integrované paměti. To umožňuje `CString` objekty, které se automaticky růst podle potřeby (to znamená, že jste si dělat starosti se rozšiřující `CString` objekt přizpůsobit delší řetězce).  
  
##  <a name="_core_cstrings_and_const_char_pointers"></a>CStrings a const char ukazatele  
 A `CString` objekt také může fungovat jako řetězcový literál stylu jazyka C ( `PCXSTR`, což je stejný jako **const char\***  Pokud není v kódování Unicode). [CSimpleStringT::operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) operátor převodu umožňuje `CString` objekty volně nahrazení ukazatele znak ve volání funkce. **CString (LPCWSTR** `pszSrc` **)** konstruktor umožňuje ukazatele znak nahrazení `CString` objekty.  
  
 Žádné pokusu o přeložení `CString` objekty. Pokud provedete dva `CString` objekty obsahující `Chicago`, například znaky v `Chicago` jsou uložené na dvou místech. (Toto nemusí platit budoucí verze knihovny MFC, proto by nemělo na ní závisí.)  
  
> [!NOTE]
>  Použití [CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) a [CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) členské funkce, když potřebujete přímý přístup k `CString` jako nonconstant ukazatel na znak.  
  
> [!NOTE]
>  Použití [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) a [CStringT::SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) členské funkce pro přidělení a nastavení `BSTR` objektům použitým v automatizace (dříve označované jako automatizace OLE).  
  
> [!NOTE]
>  Pokud je to možné, přidělit `CString` objekty rámec spíše než v haldě. To, že šetří paměť a zjednodušuje předávání parametrů.  
  
 `CString` Třída není implementovaný jako třídu kolekce Microsoft Foundation Class Library ale `CString` objekty mohou být uloženy určitě jako elementy v kolekcích.  
  
##  <a name="_core_cstring_reference_counting"></a>CString při počítání referencí  
 Od verze knihovny MFC verze 4.0 když [CStringT třída](../atl-mfc-shared/reference/cstringt-class.md) objekty se zkopírují, MFC zvýší počet odkazů místo kopírování dat. Předávání parametrů tak, že hodnota a vrácení díky `CString` objekty podle hodnoty efektivnější. Tyto operace způsobit konstruktor copy, která se má volat někdy více než jednou. Zvyšování počet odkazů snižuje režii, že pro tyto běžné operace a umožňuje pomocí `CString` více atraktivní možnosti.  
  
 Protože každá kopie zničení, se odečte počet odkazů v původní objekt. Původní `CString` objekt nebude odstraněn, dokud jeho počet odkazů se snížit na nulu.  
  
 Můžete použít `CString` členské funkce [CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) a [CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) zakázat nebo Povolit počítání odkazů.  
  
## <a name="see-also"></a>Viz také  
 [Obecná témata MFC](../mfc/general-mfc-topics.md)

