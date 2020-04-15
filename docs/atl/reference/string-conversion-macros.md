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
ms.openlocfilehash: 8df496b78334d26e7d3664642b2e9d93d6149843
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325842"
---
# <a name="string-conversion-macros"></a>Makra převodu řetězců

Tato makra poskytují funkce převodu řetězců.

## <a name="atl-and-mfc-string-conversion-macros"></a><a name="atl_and_mfc_string_conversion_macros"></a>Makra převodu řetězců knihovny ATL a knihovny MFC

Makra převodu řetězců, která jsou zde popsána, jsou platná pro knihovnu ATL i knihovnu MFC. Další informace o převodu řetězců knihovny MFC naleznete [v tématu TN059: Použití makra převodu knihovny MFC/Unicode](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md) a [maker a globálních souborů knihovny MFC](../../mfc/reference/mfc-macros-and-globals.md).

## <a name="devmode-and-textmetric-string-conversion-macros"></a><a name="devmode_and_textmetric_string_conversion_macros"></a>Makra převodu řetězců DEVMODE a TEXTMETRIC

Tato makra vytvoří kopii struktury [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) nebo [TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw) a převedou řetězce v rámci nové struktury na nový typ řetězce. Makra přidělují paměť v zásobníku pro novou strukturu a vrátí ukazatel na novou strukturu.

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>Poznámky

Příklad:

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

a:

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

V názvech maker je typ řetězce ve zdrojové struktuře vlevo (například **A**) a typ řetězce v cílové struktuře je vpravo (například **W).** A je **zkratka** pro LPSTR, **OLE** je zkratka pro LPOLESTR, **T** je zkratka pro LPTSTR a **W** zkratka pro LPWSTR.

DeVMODEA2W tedy `DEVMODE` zkopíruje strukturu s LPSTR `DEVMODE` řetězci do struktury s řetězci LPWSTR, TEXTMETRICOLE2T zkopíruje `TEXTMETRIC` strukturu s řetězci LPOLESTR do `TEXTMETRIC` struktury s lptstr řetězci a tak dále.

Dva řetězce převedené ve `DEVMODE` struktuře jsou`dmDeviceName`název zařízení (`dmFormName`) a název formuláře ( ). Makra `DEVMODE` převodu řetězců také`dmSize`aktualizují velikost struktury ( ).

Čtyři řetězce převedené ve `TEXTMETRIC` struktuře jsou`tmFirstChar`prvním znakem`tmLastChar`( ), posledním`tmDefaultChar`znakem (`tmBreakChar`), výchozím znakem ( ) a znakem konce ( ).

Chování a `DEVMODE` `TEXTMETRIC` řetězec převodu makra závisí na direktivě kompilátoru v platnosti, pokud existuje. Pokud jsou zdrojové a cílové typy stejné, nedojde k žádnému převodu. Direktivy kompilátoru mění **T** a **OLE** takto:

|Směrnice kompilátoru ve skutečnosti|T se stává|OLE se stane|
|----------------------------------|---------------|-----------------|
|Žádná|**A**|**W**|
|**\_Unicode**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|UNICODE a **OLE2ANSI** ** \_**|**W**|**A**|

V následující tabulce `DEVMODE` `TEXTMETRIC` jsou uvedena makra převodu řetězce a.

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
