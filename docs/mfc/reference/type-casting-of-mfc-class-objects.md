---
title: Přetypování objektů tříd MFC
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
ms.openlocfilehash: c7586f3c3f3aefd78fa868cc847df27e8aac58ab
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611645"
---
# <a name="type-casting-of-mfc-class-objects"></a>Přetypování objektů tříd MFC

Typ přetypování makra umožňují přetypování dané ukazatel na ukazatel, který odkazuje na objekt určité třídy, s nebo bez kontroly, přetypování je platné.

V následující tabulce jsou uvedeny makra MFC typu přetypování.

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Makra, která přetypování ukazatele na objekty tříd knihovny MFC

|||
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|Přetypování ukazatele na ukazatel na objekt třídy při kontrole, jestli je právní přetypování.|
|[STATIC_DOWNCAST](#static_downcast)|Přetypování ukazatele na objekt z jednu třídu na ukazatel souvisejícího typu. V sestavení pro ladění, způsobí ASSERT, pokud objekt není "druh" cílového typu.|

##  <a name="dynamic_downcast"></a>  DYNAMIC_DOWNCAST

Poskytuje šikovný způsob, jak přetypovat ukazatel na ukazatel na objekt třídy při kontrole, jestli je právní přetypování.

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>Parametry

*class*<br/>
Název třídy.

*pointer*<br/>
Ukazatel přetypovat na ukazatel na objekt typu *třídy*.

### <a name="remarks"></a>Poznámky

Makra bude přetypovat *ukazatel* parametr na ukazatel na objekt *třídy* typu parametru.

Pokud je objekt odkazovaný zadaným parametrem je ukazatel "druh" zjištěné třídy makro vrátí odpovídající ukazatel. Pokud není platný přetypování, vrátí makro NULL.

##  <a name="static_downcast"></a>  STATIC_DOWNCAST

Přetypování *odstraněný objekt* na ukazatel *$class_name* objektu.

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy přetypován na.

*pobject*<br/>
Převést na ukazatel na ukazatel *$class_name* objektu.

### <a name="remarks"></a>Poznámky

*odstraněný objekt* musí být buď NULL, nebo přejděte na objekt třídy, která je odvozena přímo nebo nepřímo ze *$class_name*. V sestavení vaší aplikace pomocí symbol preprocesoru _DEBUG definované makro VYHODNOCENA Pokud *odstraněný objekt* nemá hodnotu NULL, nebo pokud odkazuje na objekt, který není "druh" Třída zadaná v *class_name*parametr (viz [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). V jinou hodnotu než **_DEBUG** sestavení, makro provede bez kontroly typu přetypování.

Třída zadaná v *class_name* parametr musí být odvozen od `CObject` a musí používat DECLARE_DYNAMIC a IMPLEMENT_DYNAMIC, DECLARE_DYNCREATE a IMPLEMENT_DYNCREATE, nebo DECLARE_SERIAL a IMPLEMENT_ Sériového portu makra, jako je popsáno v článku [CObject – třída: Odvození třídy z objektu CObject](../../mfc/deriving-a-class-from-cobject.md).

Například může být přetypovat ukazatel na `CMyDoc`, označované jako `pMyDoc`, na ukazatel na `CDocument` pomocí tento výraz:

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

Pokud `pMyDoc` neukazuje na objekt odvozený přímo nebo nepřímo ze `CDocument`, bude vyhodnocení makra.

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
