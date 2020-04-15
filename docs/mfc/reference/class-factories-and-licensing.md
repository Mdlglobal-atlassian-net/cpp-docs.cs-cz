---
title: Objekty pro vytváření tříd a licencování
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: e3fed6520cdbe0fd964e4e80e7c9ed9b78296d16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372299"
---
# <a name="class-factories-and-licensing"></a>Objekty pro vytváření tříd a licencování

Chcete-li vytvořit instanci ovládacího prvku OLE, aplikace kontejneru volá členskou funkci továrny třídy ovládacího prvku. Vzhledem k tomu, že váš ovládací prvek je skutečný objekt OLE, factory třídy je zodpovědný za vytváření instancí ovládacího prvku. Každá třída ovládacího prvku OLE musí mít třídu factory.

Další důležitou vlastností ovládacích prvků OLE je jejich schopnost vynutit licenci. ControlWizard umožňuje začlenit licencování při vytváření projektu ovládacího prvku. Další informace o licencování ovládacích prvků naleznete v článku [Ovládací prvky ActiveX: Licencování ovládacího prvku ActiveX](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).

V následující tabulce je uvedeno několik maker a funkcí používaných k deklarování a implementaci třídy ovládacího prvku a k licencování ovládacího prvku.

### <a name="class-factories-and-licensing"></a>Objekty pro vytváření tříd a licencování

|||
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Deklaruje továrnu třídy pro ovládací prvek OLE nebo stránku vlastností.|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implementuje funkci `GetClassID` ovládacího prvku a deklaruje instanci factory třídy.|
|[BEGIN_OLEFACTORY](#begin_olefactory)|Začíná deklarace všech licenčních funkcí.|
|[END_OLEFACTORY](#end_olefactory)|Ukončí deklaraci všech licenčních funkcí.|
|[Soubor AfxVerifyLicFile](#afxverifylicfile)|Ověří, zda je ovládací prvek licencován pro použití v určitém počítači.|

## <a name="declare_olecreate_ex"></a><a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX

Deklaruje factory `GetClassID` třídy a členské funkce třídy ovládacího prvku.

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy ovládacího prvku.

### <a name="remarks"></a>Poznámky

Toto makro v souboru záhlaví třídy ovládacího prvku použijte pro ovládací prvek, který nepodporuje licencování.

Všimněte si, že toto makro slouží stejnému účelu jako následující ukázka kódu:

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="implement_olecreate_ex"></a><a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX

Implementuje třídy ovládacího prvku a [GetClassID](../../mfc/reference/colecontrol-class.md#getclassid) členské funkce třídy ovládacího prvku.

```
IMPLEMENT_OLECREATE_EX(
   class_name,
    external_name,
    l,
    w1,
    w2,
    b1,
    b2,
    b3,
    b4,
    b5,
    b6,
    b7,
    b8)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy stránky vlastnosti ovládacího prvku.

*external_name*<br/>
Název objektu vystavené aplikacím.

*l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8*<br/>
Součásti CLSID třídy. Další informace o těchto parametrech naleznete v poznámkách pro [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).

### <a name="remarks"></a>Poznámky

Toto makro se musí zobrazit v souboru implementace pro všechny třídy ovládacích prvku, které používají makro DECLARE_OLECREATE_EX nebo BEGIN_OLEFACTORY a END_OLEFACTORY makra. Externí název je identifikátor ovládacího prvku OLE, který je vystaven jiným aplikacím. Kontejnery používají tento název k vyžádání objektu této třídy ovládacího prvku.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="begin_olefactory"></a><a name="begin_olefactory"></a>BEGIN_OLEFACTORY

Začíná deklarace vaší třídy factory v souboru záhlaví třídy ovládacího prvku.

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Určuje název třídy ovládacího prvku, jejíž třídy factory to je.

### <a name="remarks"></a>Poznámky

Deklarace funkcí licencování třídy factory by měla začít ihned po BEGIN_OLEFACTORY.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="end_olefactory"></a><a name="end_olefactory"></a>END_OLEFACTORY

Ukončí deklaraci třídy ovládacího prvku.

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy ovládacího prvku, jehož třídy factory to je.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="afxverifylicfile"></a><a name="afxverifylicfile"></a>Soubor AfxVerifyLicFile

Volání této funkce ověřte, `pszLicFileName` zda je licenční soubor pojmenovaný podle a je platný pro ovládací prvek OLE.

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Popisovač instance dll přidružené k licencovanému ovládacímu prvku.

*pszLicFileName*<br/>
Odkazuje na řetězec znaků ukončený hodnotou null obsahující název licenčního souboru.

*pszLicFileContents*<br/>
Odkazuje na sekvenci bajtů, která se musí shodovat s posloupností nalezenou na začátku licenčního souboru.

*Cch*<br/>
Počet znaků v *pszLicFileContents*.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud licenční soubor existuje a začíná posloupností znaků v *pszLicFileContents*; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud je *cch* -1, tato funkce používá:

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
