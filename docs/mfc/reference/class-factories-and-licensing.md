---
title: Třída továrny a licencování | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5cedcedce14ce2fa6638091f0785f0456dee9891
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419740"
---
# <a name="class-factories-and-licensing"></a>Objekty pro vytváření tříd a licencování

K vytvoření instance ovládacího prvku OLE, volá aplikace typu kontejner pro členské funkce objektu pro vytváření tříd ovládacího prvku. Protože váš ovládací prvek je skutečný objekt OLE, zodpovídá za vytvoření instance ovládacího prvku objektu pro vytváření tříd. Každá třída ovládacího prvku OLE, musí mít objekt pro vytváření tříd.

Další důležitou funkcí ovládacích prvků OLE je jejich schopnost vynutit licenci. ControlWizard umožňuje začlenit licencování během vytváření projektu ovládacího prvku. Další informace o licencování ovládacích prvků, najdete v článku [ovládací prvky ActiveX: licencování ovládací prvek ActiveX](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).

Následující tabulka uvádí několik makra a funkce, které slouží k deklaraci a implementaci ovládacího prvku pro vytváření tříd a licenci ovládacího prvku.

### <a name="class-factories-and-licensing"></a>Objekty pro vytváření tříd a licencování

|||
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Deklaruje objekt pro vytváření tříd pro stránku ovládací prvek nebo vlastnost OLE.|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implementuje ovládací prvek `GetClassID` funkce a deklaruje instanci objektu pro vytváření tříd.|
|[BEGIN_OLEFACTORY](#begin_olefactory)|Začíná deklarace všechny funkce správy licencí.|
|[END_OLEFACTORY](#end_olefactory)|Ukončí deklarace všechny funkce správy licencí.|
|[Afxverifylicfile –](#afxverifylicfile)|Ověří, zda ovládací prvek je licencovaná pro použití v určitém počítači.|

##  <a name="declare_olecreate_ex"></a>  DECLARE_OLECREATE_EX

Deklaruje objekt pro vytváření tříd a `GetClassID` členské funkce třídy ovládacího prvku.

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Název třídy ovládacího prvku.

### <a name="remarks"></a>Poznámky

Použijte toto makro v souboru hlaviček třídy ovládacího prvku pro ovládací prvek, který nepodporuje licencování.

Všimněte si, že toto makro slouží stejnému účelu jako následující ukázka kódu:

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

##  <a name="implement_olecreate_ex"></a>  IMPLEMENT_OLECREATE_EX

Implementuje objekt pro vytváření tříd ovládacího prvku a [Funkce GetClassID](../../mfc/reference/colecontrol-class.md#getclassid) členské funkce třídy ovládacího prvku.

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

*$class_name*<br/>
Název třídy stránky vlastností ovládacího prvku.

*external_name*<br/>
Název objektu vystaveni aplikací.

*l, w1, w2, b1, b2, K3, b4, b5, b6, b7, b8*<br/>
Součástí CLSID pro třídu. Další informace o těchto parametrech naleznete v tématu poznámky pro [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).

### <a name="remarks"></a>Poznámky

Toto makro musí být uvedena v souboru implementace pro ovládací prvek třídy, které používá DECLARE_OLECREATE_EX – makro nebo BEGIN_OLEFACTORY a END_OLEFACTORY makra. Externí název je identifikátor ovládacího prvku OLE, který je přístupný ostatním aplikacím. Kontejnery používat tento název pro žádost o objekt této třídy ovládacího prvku.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

##  <a name="begin_olefactory"></a>  BEGIN_OLEFACTORY

Začíná deklaraci objektu pro vytváření vaší třídy v souboru hlaviček třídy vašeho ovládacího prvku.

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Určuje název třídy ovládacího prvku, jehož objekt pro vytváření tříd jde.

### <a name="remarks"></a>Poznámky

Deklarace objektu pro vytváření tříd licencování funkce chcete spustit ihned po BEGIN_OLEFACTORY.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

##  <a name="end_olefactory"></a>  END_OLEFACTORY

Ukončí deklaraci objektu pro vytváření tříd ovládacího prvku.

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Název třídy ovládacího prvku, jehož objekt pro vytváření tříd jde.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

##  <a name="afxverifylicfile"></a>  Afxverifylicfile –

Voláním této funkce zkontrolujte, že licenční soubor s názvem podle `pszLicFileName` platí pro ovládací prvek OLE.

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Popisovač instance přidružené k licencovaného ovládacího prvku knihovny DLL.

*pszLicFileName*<br/>
Odkazuje na řetězec znaků zakončené znakem null obsahující název souboru licencí.

*pszLicFileContents*<br/>
Body sekvence bajtů, který musí odpovídat pořadí nalezen na začátku souboru licencí.

*cch*<br/>
Počet znaků v *pszLicFileContents*.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bude licenční soubor existuje a začíná sekvence znaků v *pszLicFileContents*; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud *cch* -1, je tato funkce využívá:

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
