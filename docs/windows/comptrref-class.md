---
title: Comptrref – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRef class
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d4ec1139efae422035ef34030cfcffcc5547f0a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418499"
---
# <a name="comptrref-class"></a>ComPtrRef – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename T
>
class ComPtrRef : public ComPtrRefBase<T>;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
A [ComPtr\<T >](../windows/comptr-class.md) typ nebo z ní odvozené, nikoli pouze rozhraní, které jsou reprezentována `ComPtr`.

## <a name="remarks"></a>Poznámky

Představuje odkaz na objekt typu `ComPtr<T>`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[ComPtrRef::ComPtrRef – konstruktor](../windows/comptrref-comptrref-constructor.md)|Inicializuje novou instanci třídy **comptrref –** třídy z zadaný ukazatel na jiný **comptrref –** objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[ComPtrRef::GetAddressOf – metoda](../windows/comptrref-getaddressof-method.md)|Načte adresu ukazatel rozhraní reprezentované aktuální **comptrref –** objektu.|
|[ComPtrRef::ReleaseAndGetAddressOf – metoda](../windows/comptrref-releaseandgetaddressof-method.md)|Odstraní aktuální **comptrref –** objekt a vrátí ukazatel na ukazatel rozhraní, která je reprezentována **comptrref –** objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[ComPtrRef::operator InterfaceType** – operátor](../windows/comptrref-operator-interfacetype-star-star-operator.md)|Odstraní aktuální **comptrref –** objekt a vrátí ukazatel na ukazatel rozhraní, která je reprezentována **comptrref –** objektu.|
|[ComPtrRef::operator T* – operátor](../windows/comptrref-operator-t-star-operator.md)|Vrátí hodnotu [ptr_ –](../windows/comptrrefbase-ptr-data-member.md) aktuálního objektu comptrref – datový člen.|
|[ComPtrRef::operator void** – operátor](../windows/comptrref-operator-void-star-star-operator.md)|Odstraní aktuální **comptrref –** objektu, přetypování ukazatel na rozhraní, která je reprezentována **comptrref –** objektu jako ukazatel na ukazatel- **void**a pak vrátí ukazatel přetypování.|
|[ComPtrRef::operator* – operátor](../windows/comptrref-operator-star-operator.md)|Načte ukazatel na rozhraní reprezentované aktuální **comptrref –** objektu.|
|[ComPtrRef::operator== – operátor](../windows/comptrref-operator-equality-operator.md)|Určuje, zda dva **comptrref –** objekty rovnají.|
|[ComPtrRef::operator!= – operátor](../windows/comptrref-operator-inequality-operator.md)|Určuje, zda dva **comptrref –** objekty nejsou stejné.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)