---
title: Třídy objektů Factory a licencování | Microsoft Docs
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
ms.openlocfilehash: e8f411aeb88a2d76265c6e8c277b367cb1ebce57
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038227"
---
# <a name="class-factories-and-licensing"></a>Objekty pro vytváření tříd a licencování
K vytvoření instance ovládacího prvku OLE, zavolá aplikace kontejneru členské funkce ovládacího prvku třídy objektu pro vytváření. Vlastní ovládací prvek je skutečný objekt OLE, objektu pro vytváření tříd je zodpovědný za vytváření instancí ovládacího prvku. Třída ovládacích prvků každé OLE musí mít objekt pro vytváření tříd.  
  
 Další důležitou součást ovládací prvky OLE je jejich schopnost vynutit licenci. ControlWizard umožňuje začlenit licencování během vytváření projektu ovládacího prvku. Další informace o licencování řízení, najdete v článku [– ovládací prvky ActiveX: licencování ovládacího prvku ActiveX](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).  
  
 Následující tabulka uvádí několik makra a funkce, které lze deklarovat a implementovat objekt pro vytváření tříd ovládacího prvku a licencí ovládacího prvku.  
  
### <a name="class-factories-and-licensing"></a>Objekty pro vytváření tříd a licencování  
  
|||  
|-|-|  
|[DECLARE_OLECREATE_EX –](#declare_olecreate_ex)|Deklaruje třída objekt factory pro stránku OLE ovládací prvek nebo vlastnost.|  
|[IMPLEMENT_OLECREATE_EX –](#implement_olecreate_ex)|Implementuje ovládacího prvku `GetClassID` funkce a deklaruje instanci objektu pro vytváření tříd.|  
|[BEGIN_OLEFACTORY –](#begin_olefactory)|Zahájí deklaraci všechny funkce správy licencí.|  
|[END_OLEFACTORY –](#end_olefactory)|Ukončí deklaraci všechny funkce správy licencí.|  
|[Afxverifylicfile –](#afxverifylicfile)|Ověřuje, zda je ovládací prvek licenci pro použití v určitém počítači.|  
  
##  <a name="declare_olecreate_ex"></a>  DECLARE_OLECREATE_EX –  
 Deklaruje objekt pro vytváření tříd a `GetClassID` funkce člena třídy ovládacího prvku.  
  
```   
DECLARE_OLECREATE_EX(class_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Název třídy ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 Použijte toto makro v souboru řízení – třída záhlaví ovládacího prvku, který nepodporuje licencování.  
  
 Všimněte si, že tento makro slouží ke stejnému účelu jako následující ukázka kódu:  
  
 [!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="implement_olecreate_ex"></a>  IMPLEMENT_OLECREATE_EX –  
 Implementuje objekt pro vytváření tříd ovládacího prvku a [Funkce GetClassID](../../mfc/reference/colecontrol-class.md#getclassid) funkce člena třídy ovládacího prvku.  
  
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
 *class_name*  
 Název třídy stránky vlastností ovládacího prvku.  
  
 *external_name*  
 Název objektu vystavený aplikace.  
  
 *l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8*  
 Součástí třída **CLSID**. Další informace o těchto parametrů najdete v tématu poznámky pro [implement_olecreate –](run-time-object-model-services.md#implement_olecreate).  
  
### <a name="remarks"></a>Poznámky  
 Toto makro musí být v souboru implementace pro ovládací prvek třídy, které používá `DECLARE_OLECREATE_EX` makro nebo `BEGIN_OLEFACTORY` a `END_OLEFACTORY` makra. Externí název je identifikátor OLE ovládací prvek, který má přístup k jiné aplikace. Tento název kontejnery používat k vyžádání objekt této třídy ovládacího prvku.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="begin_olefactory"></a>  BEGIN_OLEFACTORY –  
 Zahájí deklarace objektu pro vytváření vaší třídy v záhlaví souboru třídy ovládacího prvku.  
  
``` 
BEGIN_OLEFACTORY(class_name)  
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Určuje název třídy ovládacího prvku jejíž zdroj tříd jde.  
  
### <a name="remarks"></a>Poznámky  
 Deklarace objektu pro vytváření tříd licencování funkce by měl začínat ihned po `BEGIN_OLEFACTORY`.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="end_olefactory"></a>  END_OLEFACTORY –  
 Ukončí deklarace objektu pro vytváření tříd ovládacího prvku.  
  
```  
END_OLEFACTORY(class_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Název třídy ovládacího prvku jejíž zdroj tříd jde.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="afxverifylicfile"></a>  Afxverifylicfile –  
 Volání této funkce můžete ověřit, že licenční soubor s názvem podle `pszLicFileName` je platný pro ovládací prvek OLE.  
  
```   
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,  
    LPCTSTR  pszLicFileName,  
    LPOLESTR  pszLicFileContents,  
    UINT cch = -1); 
```  
  
### <a name="parameters"></a>Parametry  
 *hInstance*  
 Popisovač instance knihovny DLL přidruženého k ovládacímu prvku licencované.  
  
 *pszLicFileName*  
 Odkazuje na řetězec znaků ukončené hodnotou null obsahující název souboru licencí.  
  
 *pszLicFileContents*  
 Odkazuje na pořadí bajtů, které musí odpovídat pořadí najít na začátku souboru s licencí.  
  
 *cch*  
 Počet znaků v *pszLicFileContents*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud existuje soubor licencí a začíná posloupnost znaků v *pszLicFileContents*; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *cch* -1, je tato funkce používá:  
  
 [!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]  

### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  

## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
