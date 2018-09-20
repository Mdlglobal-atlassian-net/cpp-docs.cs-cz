---
title: Comptr::CopyTo – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c9b84cbcc970183222ed06752dc61b5672615868
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405382"
---
# <a name="comptrcopyto-method"></a>ComPtr::CopyTo – metoda

Zkopíruje aktuální nebo zadané rozhraní přidružené k tomuto **ComPtr** na zadaný ukazatel.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CopyTo(
   _Deref_out_ InterfaceType** ptr
);

HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ void** ptr
) const;

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
) const;
```

### <a name="parameters"></a>Parametry

*U*<br/>
Název typu.

*ptr*<br/>
Pokud tato operace dokončí, ukazatel na požadované rozhraní.

*riid*<br/>
Identifikátor rozhraní.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, který označuje důvod, proč implicitní `QueryInterface` operace se nezdařila.

## <a name="remarks"></a>Poznámky

První funkce vrátí kopii objektu ukazatele na rozhraní přidružené k tomuto **ComPtr**. Tato funkce vždy vrátí hodnotu S_OK.

Druhá funkce provádí `QueryInterface` operace v rozhraní přidružené k tomuto **ComPtr** pro rozhraní určené typem *riid* parametru.

Třetí funkce provádí `QueryInterface` operace v rozhraní přidružené k tomuto **ComPtr** základního rozhraní *U* parametr.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[ComPtr – třída](../windows/comptr-class.md)