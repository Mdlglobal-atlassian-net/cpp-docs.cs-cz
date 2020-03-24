---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 870e3580ed23ce994d832f7c59b951680d725e41
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180495"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Specifické pro společnost Microsoft**

Zapouzdřuje nezpracovaný ukazatel rozhraní tohoto typu inteligentního ukazatele.

## <a name="syntax"></a>Syntaxe

```
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>Parametry

*pInterface*<br/>
Nezpracovaný ukazatel rozhraní.

*fAddRef*<br/>
Pokud má hodnotu TRUE, je volána `AddRef`. Pokud je hodnota FALSE, objekt `_com_ptr_t` převezme vlastnictví ukazatele nezpracovaného rozhraní bez volání `AddRef`.

## <a name="remarks"></a>Poznámky

- **Připojení (**  *pInterface*  **)** `AddRef` není voláno. Vlastnictví rozhraní je předáno tomuto objektu `_com_ptr_t`. je volána `Release` pro snížení počtu odkazů pro dříve zapouzdřený ukazatel.

- **Připojit (**  *pInterface* **,**  *fAddRef*  **)** Pokud má *fAddRef* hodnotu true, je volána `AddRef` k zvýšení počtu odkazů pro zapouzdřený ukazatel rozhraní. Pokud je *FADDREF* false, tento objekt `_com_ptr_t` převezme vlastnictví ukazatele nezpracovaného rozhraní bez volání `AddRef`. je volána `Release` pro snížení počtu odkazů pro dříve zapouzdřený ukazatel.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)
