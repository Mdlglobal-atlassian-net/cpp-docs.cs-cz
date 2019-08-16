---
title: Makra převodu řetězců
ms.date: 11/04/2016
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
ms.openlocfilehash: f7d9548fc5710e8d3d5d668dff230a60e7a291a1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495181"
---
# <a name="string-conversion-macros"></a>Makra převodu řetězců

Tato makra poskytují funkce pro převod řetězce.

##  <a name="atl_and_mfc_string_conversion_macros"></a>Makra pro převod řetězců ATL a MFC

Makra převodu řetězců popsané tady jsou platné pro ATL i MFC. Další informace o konverzi řetězců MFC naleznete v [tématu TN059: Použití převodních maker](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) MBCS/Unicode znakové sady MFC a [maker MFC a Globals](../../mfc/reference/mfc-macros-and-globals.md).

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>Makra pro převod řetězce DEVMODE a TEXTMETRIC

Tato makra vytvářejí kopii struktury [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) nebo [TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw) a převádějí řetězce v rámci nové struktury na nový typ řetězce. Makra přidělují paměť v zásobníku pro novou strukturu a vracejí ukazatel na novou strukturu.

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>Poznámky

Příklad:

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

a:

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

V názvech maker je typ řetězce ve zdrojové struktuře vlevo (například **a**) a typ řetězce v cílové struktuře je na pravé straně (například **W**). Zkratka pro typem LPStr, **OLE** představuje LPOLESTR, **T** pro LPTStr a **W** představuje LPWStr.

Proto DEVMODEA2W kopíruje `DEVMODE` strukturu s typem LPStr řetězců `DEVMODE` do struktury s `TEXTMETRIC` řetězci LPWStr, TEXTMETRICOLE2T kopíruje strukturu pomocí LPOLESTR řetězců do `TEXTMETRIC` struktury s řetězci LPTStr atd.

Dva řetězce převedené ve `DEVMODE` struktuře jsou název zařízení (`dmDeviceName`) a název formuláře (`dmFormName`). Makra převodu`dmSize`řetězce také aktualizují velikost struktury (). `DEVMODE`

Čtyři řetězce převedené ve `TEXTMETRIC` struktuře jsou první znak (`tmFirstChar`), poslední znak (`tmLastChar`), výchozí znak (`tmDefaultChar`) a znak break (`tmBreakChar`).

Chování maker převodu řetězce `DEVMODE` a `TEXTMETRIC` je závislé na direktivě kompilátoru v platném případě. Pokud jsou zdrojové a cílové typy stejné, převod se neprovádí. Direktivy kompilátoru mění **T** a **OLE** následujícím způsobem:

|Platí direktiva kompilátoru.|T se|OLE se přestanou|
|----------------------------------|---------------|-----------------|
|žádná|**A**|**W**|
|**\_SADY**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|Unicode a **OLE2ANSI**  **\_**|**W**|**A**|

V následující tabulce jsou uvedena `DEVMODE` makra `TEXTMETRIC` a převod řetězců.

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>Viz také:

[Makr](../../atl/reference/atl-macros.md)
