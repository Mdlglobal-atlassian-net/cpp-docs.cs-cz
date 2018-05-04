---
title: Řetězce makra převodů | Microsoft Docs
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
ms.openlocfilehash: 917afc7dae7a0ed96d5d5cc476b4f8394abe8913
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="string-conversion-macros"></a>Řetězce makra převodů

Tyto makra zadejte řetězec funkce pro převod.  
 
##  <a name="atl_and_mfc_string_conversion_macros"></a>  ATL a MFC řetězec převodních maker

Makra převodů řetězec tady popisovaných jsou platné pro ATL a MFC. Další informace o převod řetězce MFC najdete v tématu [TN059: použití převodních maker MBCS/Unicode MFC](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) a [MFC – makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md).

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>  DEVMODE a makra převodů TEXTMETRIC řetězec

Tyto makra vytvořit kopii [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) nebo [TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132) struktury a převod řetězců v rámci nové struktury na nový typ řetězec. Makra přidělit paměť v zásobníku pro novou strukturu a vrátí ukazatel na strukturu nové.  
  
```cpp
MACRONAME( address_of_structure )
```  
  
### <a name="remarks"></a>Poznámky

Příklad:  
  
[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]  
  
a:  
  
[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]  
  
V názvech makro na řetězcový typ. ve struktuře zdroj je na levé straně (například **A**) a typ řetězce ve struktuře cílové je na pravé straně (například **W**). **A** znamená `LPSTR`, **OLE** znamená `LPOLESTR`, **T** znamená `LPTSTR`, a **W** znamená `LPWSTR`.  
  
Proto **DEVMODEA2W** kopie `DEVMODE` struktury s `LPSTR` řetězce do `DEVMODE` struktury s `LPWSTR` řetězce, **TEXTMETRICOLE2T** zkopíruje `TEXTMETRIC`struktury s `LPOLESTR` řetězce do `TEXTMETRIC` struktury s `LPTSTR` řetězce a tak dále.  
  
Dva řetězce v převést `DEVMODE` struktura jsou název zařízení (`dmDeviceName`) a název formuláře (`dmFormName`). `DEVMODE` Makra převodů řetězec také aktualizovat velikost struktury (`dmSize`).  
  
Čtyři řetězce převést v `TEXTMETRIC` struktura jsou první znak (`tmFirstChar`), jeho poslední znak (`tmLastChar`), výchozí znakovou (`tmDefaultChar`) a znak konce (`tmBreakChar`).
  
Chování `DEVMODE` a `TEXTMETRIC` makra převodů řetězec závisí na direktivy kompilátoru vliv, pokud existuje. Pokud zdrojové a cílové typy jsou stejné, žádný převod probíhá. Direktivy kompilátoru změnit **T** a **OLE** následujícím způsobem:  
  
|Kompilátor – direktiva v platnost|Změní T|Změní OLE|  
|----------------------------------|---------------|-----------------|  
|žádná|**A**|**W**|  
|**\_KÓDOVÁNÍ UNICODE**|**W**|**W**|  
|**OLE2ANSI**|**A**|**A**|  
|**\_UNICODE** a **OLE2ANSI**|**W**|**A**|  
  
 Následující tabulka uvádí `DEVMODE` a `TEXTMETRIC` řetězce makra převodů.  
  
|||  
|-|-|  
|`DEVMODEA2W`|`TEXTMETRICA2W`|  
|`DEVMODEOLE2T`|`TEXTMETRICOLE2T`|  
|`DEVMODET2OLE`|`TEXTMETRICT2OLE`|  
|`DEVMODEW2A`|`TEXTMETRICW2A`|  

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
