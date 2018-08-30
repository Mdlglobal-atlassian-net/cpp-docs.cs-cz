---
title: Makra převodu řetězců | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
dev_langs:
- C++
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d9c4c43098d7f0ca8a5e9588a69a47d6e98a066
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210052"
---
# <a name="string-conversion-macros"></a>Makra převodu řetězců

Tato makra poskytují funkce pro převod řetězce.  
 
##  <a name="atl_and_mfc_string_conversion_macros"></a>  ATL a MFC – makra převodu řetězců

Makra převodů řetězec popsaném jsou platné pro knihovny ATL a MFC. Další informace o převodu řetězce knihovny MFC naleznete v tématu [TN059: použití převodních maker MBCS/Unicode MFC](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) a [v makrech MFC a Globals](../../mfc/reference/mfc-macros-and-globals.md).

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>  DEVMODE a makra převodů TEXTMETRIC řetězec

Vytvořte kopii těchto maker [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) nebo [TEXTMETRIC](/windows/desktop/api/wingdi/ns-wingdi-tagtextmetrica) struktury a převod řetězců v rámci nové struktury na nový typ řetězec. Makra přidělení paměti na zásobníku pro novou strukturu a vrácen ukazatel na novou strukturu.  
  
```cpp
MACRONAME( address_of_structure )
```  
  
### <a name="remarks"></a>Poznámky

Příklad:  
  
[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]  
  
a:  
  
[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]  
  
V názvech – makro je typ řetězce ve struktuře zdroje na levé straně (například **A**) a typ řetězce ve struktuře cíl je na pravé straně (například **W**). **A** zastupuje LPSTR, **OLE** zastupuje LPOLESTR, **T** zastupuje LPTSTR, a **W** zastupuje LPWSTR.  
  
Proto DEVMODEA2W zkopíruje `DEVMODE` strukturu s typem LPSTR řetězce do `DEVMODE` struktura s řetězci LPWSTR, TEXTMETRICOLE2T kopie `TEXTMETRIC` strukturu s LPOLESTR řetězce do `TEXTMETRIC` struktury s řetězci LPTSTR a tak dále.  
  
Dva řetězce převedeny do `DEVMODE` struktury jsou názvu zařízení (`dmDeviceName`) a název formuláře (`dmFormName`). `DEVMODE` Makra převodu řetězců také aktualizovat velikost struktury (`dmSize`).  
  
Čtyři řetězce převedeny do `TEXTMETRIC` struktury jsou prvním znakem (`tmFirstChar`), poslední znak (`tmLastChar`), výchozí znak (`tmDefaultChar`) a znak konce (`tmBreakChar`).
  
Chování `DEVMODE` a `TEXTMETRIC` makra převodu řetězců závisí na direktivy kompilátoru účinek, pokud existuje. Pokud zdrojové a cílové typy jsou stejné, se provádí převod. Direktivy kompilátoru změnit **T** a **OLE** následujícím způsobem:  
  
|Direktivy kompilátoru platná|Změní T|Změní OLE|  
|----------------------------------|---------------|-----------------|  
|žádná|**A**|**W**|  
|**\_KÓDOVÁNÍ UNICODE**|**W**|**W**|  
|**OLE2ANSI**|**A**|**A**|  
|**\_Kódování UNICODE** a **OLE2ANSI**|**W**|**A**|  
  
 Následující tabulce jsou uvedeny `DEVMODE` a `TEXTMETRIC` makra převodu řetězců.  
  
|||  
|-|-|  
|DEVMODEA2W|TEXTMETRICA2W|  
|DEVMODEOLE2T|TEXTMETRICOLE2T|  
|DEVMODET2OLE|TEXTMETRICT2OLE|  
|DEVMODEW2A|TEXTMETRICW2A|  

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
