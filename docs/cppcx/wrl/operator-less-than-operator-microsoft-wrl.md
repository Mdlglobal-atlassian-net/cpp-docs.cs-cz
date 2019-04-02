---
title: operátor&lt; – operátor (Microsoft::WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator<
ms.assetid: bfae0e1c-1648-482b-99c2-3217d62aba46
ms.openlocfilehash: 8b9d9936eabb75b58eabde487db8d1eb42abc9dd
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786883"
---
# <a name="operatorlt-operator-microsoftwrl"></a>operátor&lt; – operátor (Microsoft::WRL)

Určuje, zda je adresa jeden objekt menší než jiný.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T, class U>
bool operator<(const ComPtr<T>& a, const ComPtr<U>& b) throw();
template<class T, class U>
bool operator<(const Details::ComPtrRef<ComPtr<T>>& a, const Details::ComPtrRef<ComPtr<U>>& b) throw();
```

### <a name="parameters"></a>Parametry

*a*<br/>
Levý objekt.

*b*<br/>
Pravý objekt.

## <a name="return-value"></a>Návratová hodnota

**true** Pokud adresa *a* je menší než adresu *b*; v opačném případě **false**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)