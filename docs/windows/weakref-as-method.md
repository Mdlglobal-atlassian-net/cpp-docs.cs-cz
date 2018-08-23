---
title: Weakref::AS – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::As
dev_langs:
- C++
helpviewer_keywords:
- As method
ms.assetid: 7173da62-b3fe-44d6-aea4-1aa97e69b221
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2a56904fb3709137c167513d0eba426bda7ad14
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589366"
---
# <a name="weakrefas-method"></a>WeakRef::As – metoda

Nastaví zadaný `ComPtr` parametr ukazatele k reprezentaci zadané rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* ptr
);

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr
);
```

### <a name="parameters"></a>Parametry

*U*  
Identifikátor rozhraní.

*ptr*  
Když tato operace dokončí, objekt, který představuje parametr *U*.

## <a name="return-value"></a>Návratová hodnota

- Pokud je tato operace úspěšná; S_OK v opačném případě HRESULT, který označuje důvod operace nebyla úspěšná, a *ptr* je nastavena na **nullptr**.

- Pokud tato operace úspěšná, ale aktuální S_OK **WeakRef** objekt již byl uvolněn. Parametr *ptr* je nastavena na **nullptr**.

- Pokud tato operace úspěšná, ale aktuální S_OK **WeakRef** objekt není odvozen z parametru *U*. Parametr *ptr* je nastavena na **nullptr**.

## <a name="remarks"></a>Poznámky

Je vygenerován chybu, pokud parametr *U* je `IWeakReference`, nebo není odvozen od `IInspectable`.

První šablona je formulář, který by měl používat ve vašem kódu. Druhá šablona se osobní a specializace pomocné rutiny, podporující funkcí jazyka C++, jako [automaticky](../cpp/auto-cpp.md) klíčovým slovem odvození typu.

Od verze Windows 10 SDK, tato metoda nenastaví **WeakRef** instance na **nullptr** Pokud nebylo možné získat nestálý odkaz, takže byste se měli vyhnout kontroly chyb kódu, která kontroluje WeakRef pro **nullptr**. Místo toho zkontrolujte *ptr* pro **nullptr**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[WeakRef – třída](../windows/weakref-class.md)