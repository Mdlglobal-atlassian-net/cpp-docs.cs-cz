---
title: Programování pomocí třídy CComBSTR (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b957cca4ff1af93d3f62ab0bf667462c91b81bba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="programming-with-ccombstr-atl"></a>Programování pomocí třídy CComBSTR (ATL)
Třídy ATL [CComBSTR](../atl/reference/ccombstr-class.md) poskytuje obálku kolem `BSTR` datového typu. Při `CComBSTR` je užitečným nástrojem, existuje několik situací, které vyžadují upozornění.  
  
-   [Problémy při převodu](#programmingwithccombstr_conversionissues)  
  
-   [Obor problémy](#programmingwithccombstr_scopeissues)  
  
-   [Explicitní uvolnění objektu CComBSTR](#programmingwithccombstr_explicitlyfreeing)  
  
-   [Pomocí třídy CComBSTR objekty v smyčky](#programmingwithccombstr_usingloops)  
  
-   [Problémy s nevrácenou pamětí](#programmingwithccombstr_memoryleaks)  
  
##  <a name="programmingwithccombstr_conversionissues"></a> Problémy při převodu  
 I když několik `CComBSTR` metody automaticky převede argument řetězec ANSI do kódu Unicode, metody vždy vrátí řetězce formátu Unicode. Převést ANSI výstupní řetězec, použijte třídu knihovny ATL převod. Další informace o převodu třídy ATL najdete v tématu [ATL a MFC makra převodů řetězec](reference/string-conversion-macros.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]  
  
 Pokud používáte řetězcový literál upravit `CComBSTR` objektu, použijte široká znaková řetězce. Tím se sníží nepotřebné převody.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]  
  
##  <a name="programmingwithccombstr_scopeissues"></a> Obor problémy  
 Stejně jako u jakékoli dobře behaved třída `CComBSTR` uvolní jeho prostředky, když probíhá mimo rozsah. Pokud vrátí ukazatel na funkci `CComBSTR` řetězec, to může způsobit problémy, jako je ukazatel bude odkazovat na paměti, který již byl uvolněn. V těchto případech použít **kopie** metoda, jak je uvedeno níže.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]  
  
##  <a name="programmingwithccombstr_explicitlyfreeing"></a> Explicitní uvolnění objektu CComBSTR  
 Je možné explicitně uvolnit řetězec součástí `CComBSTR` objektu před objekt nedostane mimo rozsah. Pokud po uvolnění řetězec `CComBSTR` objekt je neplatný.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]  
  
##  <a name="programmingwithccombstr_usingloops"></a> Pomocí třídy CComBSTR objekty v smyčky  
 Jako `CComBSTR` třída přiděluje vyrovnávací paměti k provádění některých operací, jako `+=` operátor nebo **připojení** metoda, nedoporučuje se provést zacházení s řetězci uvnitř úzkou smyčky. V těchto situacích `CStringT` poskytuje lepší výkon.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]  
  
##  <a name="programmingwithccombstr_memoryleaks"></a> Problémy s nevrácenou pamětí  
 Předávání na adresu inicializovali `CComBSTR` fungovat jako **[out]** parametr způsobí, že nevrácenou pamětí.  
  
 V následujícím příkladu řetězec přiděleno řetězec `"Initialized"` došlo při k úniku funkce `MyGoodFunction` nahrazuje řetězec.  
  
 [!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]  
  
 Abyste se vyhnuli nevracení paměti, volání **prázdný** metoda na existující `CComBSTR` objekty před předáním adresy jako **[out]** parametr.  
  
 Všimněte si, že stejný kód by způsobit, že pokud byl parametr funkce **[v, out]**.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../atl/active-template-library-atl-concepts.md)   
 [CStringT – třída](../atl-mfc-shared/reference/cstringt-class.md)   
 [wstring](../standard-library/basic-string-class.md)   
 [Makra převodu řetězců](../atl/reference/string-conversion-macros.md)

