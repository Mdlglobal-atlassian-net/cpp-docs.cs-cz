---
title: Objekty pro vytváření tříd a licencování
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: 18d86122e57af056a50a4d94bac89d65a7b71c7d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855720"
---
# <a name="class-factories-and-licensing"></a>Objekty pro vytváření tříd a licencování

Chcete-li vytvořit instanci ovládacího prvku OLE, kontejnerová aplikace volá členskou funkci objektu factory třídy ovládacího prvku. Vzhledem k tomu, že váš ovládací prvek je skutečný objekt OLE, je objekt factory třídy zodpovědný za vytváření instancí vašeho ovládacího prvku. Každá třída ovládacího prvku OLE musí mít objekt factory třídy.

Další důležitou funkcí ovládacích prvků OLE je jejich schopnost vymáhat licenci. ControlWizard umožňuje začlenit licencování během vytváření projektu řízení. Další informace o řízení licencování najdete v článku [ovládací prvky ActiveX: licencování ovládacího prvku ActiveX](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).

Následující tabulka uvádí několik maker a funkcí, které slouží k deklaraci a implementaci objektu pro vytváření tříd ovládacího prvku a k licencování vašeho ovládacího prvku.

### <a name="class-factories-and-licensing"></a>Objekty pro vytváření tříd a licencování

|||
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Deklaruje objekt pro vytváření tříd pro ovládací prvek OLE nebo stránku vlastností.|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implementuje funkci `GetClassID` ovládacího prvku a deklaruje instanci objektu pro vytváření tříd.|
|[BEGIN_OLEFACTORY](#begin_olefactory)|Zahájí deklaraci všech licenčních funkcí.|
|[END_OLEFACTORY](#end_olefactory)|Ukončí deklaraci všech licenčních funkcí.|
|[AfxVerifyLicFile](#afxverifylicfile)|Ověřuje, zda je ovládací prvek licencován pro použití v určitém počítači.|

##  <a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX

Deklaruje objekt pro vytváření tříd a členskou funkci `GetClassID` vaší třídy ovládacího prvku.

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy ovládacího prvku

### <a name="remarks"></a>Poznámky

Použijte toto makro v souboru hlaviček třídy ovládacího prvku pro ovládací prvek, který nepodporuje licencování.

Všimněte si, že toto makro slouží stejnému účelu jako následující ukázka kódu:

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>Požadavky

  **Header** AFXCTL. h

##  <a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX

Implementuje objekt pro vytváření tříd ovládacího prvku a členskou funkci [GetClassID](../../mfc/reference/colecontrol-class.md#getclassid) vaší třídy ovládacího prvku.

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
Název třídy stránky vlastností ovládacího prvku

*external_name*<br/>
Název objektu vystavený aplikacím.

*l, W1, W2, B1, B2, B3, B4, B5, B6, B7, B8*<br/>
Komponenty CLSID třídy. Další informace o těchto parametrech naleznete v tématu poznámky k [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).

### <a name="remarks"></a>Poznámky

Toto makro se musí nacházet v implementačním souboru pro jakoukoliv třídu ovládacího prvku, která používá makro DECLARE_OLECREATE_EX nebo makra BEGIN_OLEFACTORY a END_OLEFACTORY. Externí název je identifikátor ovládacího prvku OLE, který je vystavený ostatním aplikacím. Kontejnery používají tento název k vyžádání objektu této třídy ovládacího prvku.

### <a name="requirements"></a>Požadavky

  **Header** AFXCTL. h

##  <a name="begin_olefactory"></a>BEGIN_OLEFACTORY

Zahájí deklaraci vašeho objektu pro vytváření tříd v hlavičkovém souboru vaší třídy ovládacího prvku.

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Určuje název třídy ovládacího prvku, jejíž objekt pro vytváření tříd je to.

### <a name="remarks"></a>Poznámky

Deklarace funkcí licencování factory třídy by měly začít hned po BEGIN_OLEFACTORY.

### <a name="requirements"></a>Požadavky

  **Header** AFXCTL. h

##  <a name="end_olefactory"></a>END_OLEFACTORY

Ukončí deklaraci objektu factory třídy ovládacího prvku.

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy ovládacího prvku, jejíž objekt pro vytváření tříd je to.

### <a name="requirements"></a>Požadavky

  **Header** AFXCTL. h

##  <a name="afxverifylicfile"></a>AfxVerifyLicFile

Voláním této funkce ověříte, že licenční soubor nazvaný `pszLicFileName` je platný pro ovládací prvek OLE.

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Obslužná rutina instance knihovny DLL přidružené k Licencovanému ovládacímu prvku.

*pszLicFileName*<br/>
Odkazuje na řetězec znaků zakončený hodnotou null obsahující název souboru licence.

*pszLicFileContents*<br/>
Odkazuje na sekvenci bajtů, která musí odpovídat sekvenci nalezené na začátku licenčního souboru.

*cch*<br/>
Počet znaků v *pszLicFileContents*.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud soubor s licencí existuje a začíná sekvencí znaků v *pszLicFileContents*; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud je *CCH* -1, tato funkce používá:

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** AFXCTL. h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
