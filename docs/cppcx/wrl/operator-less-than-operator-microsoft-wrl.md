---
title: 'operator&lt; – operátor (Microsoft:: WRL)'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator<
ms.assetid: bfae0e1c-1648-482b-99c2-3217d62aba46
ms.openlocfilehash: 04f5598667f7e0e036f0a55cd3f9cc52b5356299
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213639"
---
# <a name="operatorlt-operator-microsoftwrl"></a>operator&lt; – operátor (Microsoft:: WRL)

Určuje, zda je adresa jednoho objektu menší než jiná.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T, class U>
bool operator<(const ComPtr<T>& a, const ComPtr<U>& b) throw();
template<class T, class U>
bool operator<(const Details::ComPtrRef<ComPtr<T>>& a, const Details::ComPtrRef<ComPtr<U>>& b) throw();
```

### <a name="parameters"></a>Parametry

*určitého*<br/>
Levý objekt

*b*<br/>
Pravý objekt.

## <a name="return-value"></a>Návratová hodnota

**true** , pokud je adresa *a* menší než adresa *b*; v opačném případě **false**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Client. h

**Obor názvů:** Microsoft:: WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)
