---
title: Programování pomocí třídy CComBSTR (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
ms.openlocfilehash: 020c2d18c721e658d15bb1451039154ae50b99f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321798"
---
# <a name="programming-with-ccombstr-atl"></a>Programování pomocí třídy CComBSTR (ATL)

Atl třídy [CComBSTR](../atl/reference/ccombstr-class.md) poskytuje obálku kolem datového typu BSTR. Zatímco `CComBSTR` je užitečným nástrojem, existuje několik situací, které vyžadují opatrnost.

- [Problémy s převodem](#programmingwithccombstr_conversionissues)

- [Problémy s rozsahem](#programmingwithccombstr_scopeissues)

- [Explicitní uvolnění objektu CComBSTR](#programmingwithccombstr_explicitlyfreeing)

- [Použití objektů CComBSTR ve smyčkách](#programmingwithccombstr_usingloops)

- [Problémy s nevracením paměti](#programmingwithccombstr_memoryleaks)

## <a name="conversion-issues"></a><a name="programmingwithccombstr_conversionissues"></a>Problémy s převodem

Přestože `CComBSTR` několik metod automaticky převede argument řetězce ANSI na unicode, metody vždy vrátí formátovací řetězce Unicode. Chcete-li převést výstupní řetězec zpět na ANSI, použijte třídu převodu ATL. Další informace o třídách převodu knihovny ATL naleznete v tématu [ATL a MFC String Conversion Macros](reference/string-conversion-macros.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]

Pokud používáte literál řetězce `CComBSTR` k úpravě objektu, použijte řetězce širokých znaků. Tím se sníží zbytečné převody.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]

## <a name="scope-issues"></a><a name="programmingwithccombstr_scopeissues"></a>Problémy s rozsahem

Stejně jako u všech dobře `CComBSTR` vychovaných tříd, uvolní své prostředky, když přejde mimo rozsah. Pokud funkce vrátí ukazatel `CComBSTR` na řetězec, to může způsobit problémy, jako ukazatel bude odkazovat na paměť, která již byla uvolněna. V těchto případech `Copy` použijte metodu, jak je znázorněno níže.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]

## <a name="explicitly-freeing-the-ccombstr-object"></a><a name="programmingwithccombstr_explicitlyfreeing"></a>Explicitní uvolnění objektu CComBSTR

Je možné explicitně uvolnit řetězec obsažený `CComBSTR` v objektu před objektem zhasne obor. Pokud je řetězec uvolněn, `CComBSTR` objekt je neplatný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]

## <a name="using-ccombstr-objects-in-loops"></a><a name="programmingwithccombstr_usingloops"></a>Použití objektů CComBSTR ve smyčkách

Jako `CComBSTR` třída přiděluje vyrovnávací paměť k `+=` provedení `Append` určité operace, jako je například operátor nebo metoda, není doporučeno provádět manipulaci s řetězci uvnitř těsné smyčky. V těchto `CStringT` situacích poskytuje lepší výkon.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]

## <a name="memory-leak-issues"></a><a name="programmingwithccombstr_memoryleaks"></a>Problémy s nevracením paměti

Předání adresy inicializované `CComBSTR` funkce jako **parametru [out]** způsobí nevracení paměti.

V níže uvedeném příkladu řetězec přidělený k uložení `"Initialized"` `MyGoodFunction` řetězce nevracení, když funkce nahradí řetězec.

[!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]

Chcete-li se vyhnout `Empty` nevracení, volání metody na existující `CComBSTR` objekty před předáním adresu jako **[out]** parametr.

Všimněte si, že stejný kód by nezpůsobil nevracení, pokud parametr funkce byl **[in, out]**.

## <a name="see-also"></a>Viz také

[Koncepty](../atl/active-template-library-atl-concepts.md)<br/>
[CStringT – třída](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[wstring](../standard-library/basic-string-class.md)<br/>
[Makra převodu řetězců](../atl/reference/string-conversion-macros.md)
