---
title: Weakref::asiid – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 94e87309-32da-4dbb-8233-e77313a1f448
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8844828028e174bd216bddb7e7c82cc9e5971a90
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594880"
---
# <a name="weakrefasiid-method"></a>WeakRef::AsIID – metoda

Nastaví zadaný `ComPtr` parametr ukazatele představující ID zadané rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>Parametry

*riid*  
Identifikátor rozhraní.

*ptr*  
Když tato operace dokončí, objekt, který představuje parametr *riid*.

## <a name="return-value"></a>Návratová hodnota

- Pokud je tato operace úspěšná; S_OK v opačném případě HRESULT, který označuje důvod operace nebyla úspěšná, a *ptr* je nastavena na **nullptr**.

- Pokud tato operace úspěšná, ale aktuální S_OK **WeakRef** objekt již byl uvolněn. Parametr *ptr* je nastavena na **nullptr**.

- Pokud tato operace úspěšná, ale aktuální S_OK **weakref –** objekt není odvozen z parametru *riid*. Parametr *ptr* je nastavena na **nullptr**. (Další informace najdete v části poznámky.)

## <a name="remarks"></a>Poznámky

Je vygenerován chybu, pokud parametr *riid* není odvozen od `IInspectable`. Tato chyba nahrazuje návratovou hodnotu.

První šablona je formulář, který by měl používat ve vašem kódu. Druhá šablona (není vidět, ale deklarované v souboru hlaviček) je interní, specializace pomocné rutiny, podporující funkcí jazyka C++, jako [automaticky](../cpp/auto-cpp.md) klíčovým slovem odvození typu.

Od verze Windows 10 SDK, tato metoda nenastaví **WeakRef** instance na **nullptr** Pokud nebylo možné získat nestálý odkaz, takže byste se měli vyhnout kontroly chyb kódu, který kontroluje, **WeakRef** pro **nullptr**. Místo toho zkontrolujte *ptr* pro **nullptr**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[WeakRef – třída](../windows/weakref-class.md)