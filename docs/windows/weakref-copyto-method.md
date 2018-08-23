---
title: Weakref::CopyTo – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: f83de6da-b3d4-41a6-9845-cd725ecf3b75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 791e9040d9e35c7dfb657cca38e26c01e86c86c4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594418"
---
# <a name="weakrefcopyto-method"></a>WeakRef::CopyTo – metoda

Přiřadí ukazatel rozhraní, pokud je k dispozici k proměnné zadané ukazatele.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ IInspectable** ptr
);

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
);

HRESULT CopyTo(
   _Deref_out_ IWeakReference** ptr
);
```

### <a name="parameters"></a>Parametry

*U*  
Ukazatel `IInspectable` rozhraní. Je vygenerován chybu, pokud *U* není odvozen od `IInspectable`.

*riid*  
Identifikátor rozhraní. Je vygenerován chybu, pokud *riid* není odvozen od `IWeakReference`.

*ptr*  
Dvakrát nepřímé ukazatel na `IInspectable` nebo `IWeakReference`.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby. Další informace najdete v tématu **poznámky**.

## <a name="remarks"></a>Poznámky

Vrácená hodnota S_OK znamená, že tato operace proběhla úspěšně, ale neukazuje, jestli se přeložila na silný odkaz nestálý odkaz. Pokud se vrátí hodnotu S_OK, otestujte tento parametr *p* je silný odkaz; to znamená, že parametr *p* není roven **nullptr**.

Od verze Windows 10 SDK, tato metoda nenastaví **WeakRef** instance na **nullptr** Pokud nebylo možné získat nestálý odkaz, takže byste se měli vyhnout Chyba při kontrole kódu, který kontroluje WeakRef pro **nullptr**. Místo toho zkontrolujte *ptr* pro **nullptr**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[WeakRef – třída](../windows/weakref-class.md)