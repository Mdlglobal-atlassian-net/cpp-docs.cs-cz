---
title: Programování pomocí třídy CComBSTR (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
ms.openlocfilehash: 44689b45d567c524d6db1446cd65201c21499c91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633113"
---
# <a name="programming-with-ccombstr-atl"></a>Programování pomocí třídy CComBSTR (ATL)

ATL – třídy [CComBSTR](../atl/reference/ccombstr-class.md) poskytuje obálku kolem datový typ BSTR. Zatímco `CComBSTR` je užitečný nástroj, existuje několik situací, které vyžadují upozornění.

- [Problémy při převodu](#programmingwithccombstr_conversionissues)

- [Obor problémy](#programmingwithccombstr_scopeissues)

- [Explicitní uvolnění objektu CComBSTR](#programmingwithccombstr_explicitlyfreeing)

- [Pomocí třídy CComBSTR objekty ve smyčkách](#programmingwithccombstr_usingloops)

- [Problémy nevracení paměti](#programmingwithccombstr_memoryleaks)

##  <a name="programmingwithccombstr_conversionissues"></a> Problémy při převodu

I když několik `CComBSTR` metody automaticky převede argument řetězce ANSI na Unicode, metody vždy vrátí formátovací řetězce Unicode. Výstupní řetězec převést zpět na ANSI, použijte třídy knihovny ATL převodu. Další informace o převodu třídy ATL naleznete v tématu [knihovny ATL a MFC – makra převodu řetězců](reference/string-conversion-macros.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]

Pokud používáte k úpravě řetězcového literálu `CComBSTR` objektu, pomocí řetězce širokého znaku. Tím se sníží zbytečné převody.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]

##  <a name="programmingwithccombstr_scopeissues"></a> Obor problémy

Stejně jako u jakékoli třídy dobře behaved `CComBSTR` uvolníte její prostředky, když dostane mimo rozsah. Pokud funkce vrátí ukazatel `CComBSTR` řetězec, to může způsobit potíže, jak bude ukazatel odkazovat paměti, který již byl uvolněn. V těchto případech použijte `Copy` způsob, jak je znázorněno níže.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]

##  <a name="programmingwithccombstr_explicitlyfreeing"></a> Explicitní uvolnění objektu CComBSTR

Je možné explicitně uvolnit řetězec obsažený v `CComBSTR` objektu předtím, než objekt dostane mimo rozsah. Pokud řetězec je uvolněn, `CComBSTR` objekt je neplatný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]

##  <a name="programmingwithccombstr_usingloops"></a> Pomocí třídy CComBSTR objekty ve smyčkách

Jako `CComBSTR` třídy přidělí vyrovnávací paměť k provádění určitých operací, jako `+=` operátor nebo `Append` metody není doporučeno, abyste provedli zacházení s řetězci v těsné smyčce. V těchto situacích `CStringT` poskytuje lepší výkon.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]

##  <a name="programmingwithccombstr_memoryleaks"></a> Problémy nevracení paměti

Předávání na adresu inicializovali `CComBSTR` fungovat jako **[out]** parametr způsobí, že nevracení paměti.

V následujícím příkladu řetězec přidělené pro uložení řetězce `"Initialized"` úniku při funkce `MyGoodFunction` nahradí řetězec.

[!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]

Chcete-li zabránit nevracení paměti, zavolejte `Empty` metodu na existující `CComBSTR` objekty před předáním adresy jako **[out]** parametr.

Všimněte si, že stejný kód by způsobit, že pokud byl parametr funkce **[v, out]**.

## <a name="see-also"></a>Viz také

[Koncepty](../atl/active-template-library-atl-concepts.md)<br/>
[CStringT – třída](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[wstring](../standard-library/basic-string-class.md)<br/>
[Makra převodu řetězců](../atl/reference/string-conversion-macros.md)

