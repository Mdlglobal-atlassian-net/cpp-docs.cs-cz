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
ms.openlocfilehash: 953acc32c3510b31c265f2d64d0a013f6dee06cc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372895"
---
# <a name="type-casting-of-mfc-class-objects"></a>Přetypování objektů tříd MFC

Typ přetypování makra poskytují způsob, jak přetypovat daný ukazatel na ukazatel, který odkazuje na objekt určité třídy, s nebo bez kontroly, zda přetypování je legální.

V následující tabulce jsou uvedena makra přetypování typu knihovny MFC.

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Makra, která přetypovává ukazatele na objekty třídy knihovny MFC

|||
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|Předává ukazatel na ukazatel na objekt třídy při kontrole, pokud je přetypování legální.|
|[STATIC_DOWNCAST](#static_downcast)|Předává ukazatel na objekt z jedné třídy na ukazatel souvisejícího typu. V sestavení ladění způsobí ASSERT, pokud objekt není "druh" cílový typ.|

## <a name="dynamic_downcast"></a><a name="dynamic_downcast"></a>DYNAMIC_DOWNCAST

Poskytuje praktický způsob, jak přetypovat ukazatel na ukazatel na objekt třídy při kontrole, pokud je přetypování legální.

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>Parametry

*třída*<br/>
Název třídy.

*ukazatel*<br/>
Ukazatel, který má být přetypován na ukazatel na objekt *třídy*typu .

### <a name="remarks"></a>Poznámky

Makro přenese parametr *ukazatele* na ukazatel na objekt typu parametru *třídy.*

Pokud je objekt odkazovaný ukazatelem "druh" identifikované třídy, makro vrátí příslušný ukazatel. Pokud se nejedná o legální přetypování, makro vrátí hodnotu NULL.

## <a name="static_downcast"></a><a name="static_downcast"></a>STATIC_DOWNCAST

Přetypovat *pobject* k ukazateli *na class_name* objekt.

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy, která je obsazena do.

*pobjekt*<br/>
Ukazatel, který má být přetypován na ukazatel na *class_name* objekt.

### <a name="remarks"></a>Poznámky

*pobjekt* musí být null nebo přejděte na objekt třídy, který je odvozen přímo nebo nepřímo z *class_name*. V sestavení aplikace s definovaným _DEBUG symbolem preprocesoru makro bude ASSERT, pokud *pobjekt* není NULL, nebo pokud odkazuje na objekt, který není "druh" třídy zadané v *parametru class_name* (viz [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). V sestaveních **bez _DEBUG** makro provádí přetypování bez kontroly typu.

Třída zadaná v *parametru* class_name `CObject` musí být odvozena od a musí používat DECLARE_DYNAMIC a IMPLEMENT_DYNAMIC, DECLARE_DYNCREATE a IMPLEMENT_DYNCREATE nebo makra DECLARE_SERIAL a IMPLEMENT_SERIAL, jak je vysvětleno v článku [CObject Class: Deriving a Class from CObject](../../mfc/deriving-a-class-from-cobject.md).

Můžete například přetypovat `CMyDoc`ukazatel `pMyDoc`na , nazvaný , na ukazatel na `CDocument` použití tohoto výrazu:

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

Pokud `pMyDoc` neukazuje na objekt odvozený přímo `CDocument`nebo nepřímo z , makro bude ASSERT.

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
