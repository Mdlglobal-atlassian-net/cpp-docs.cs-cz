---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 057d784bb495aefaeec1b86697a7421f6464cbd7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745067"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Specifické pro Microsoft**

Zapouzdřuje ukazatel nezpracovanérozhraní tohoto inteligentního ukazatele typu.

## <a name="syntax"></a>Syntaxe

```cpp
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>Parametry

*pRozhraní*<br/>
Nezpracovaný ukazatel rozhraní.

*fAddRef*<br/>
Pokud je TRUE, `AddRef` pak se nazývá. Pokud je FALSE, `_com_ptr_t` objekt převezme vlastnictví ukazatele nezpracované rozhraní bez volání `AddRef`.

## <a name="remarks"></a>Poznámky

- **Připojit(**  *pInterface*  **)** `AddRef` není volána. Vlastnictví rozhraní je předán a `_com_ptr_t` tento objekt. `Release`je volána k snížení počtu odkazů pro dříve zapouzdřený ukazatel.

- **Připojit(**  *pInterface* **,**  *fAddRef*  **)** Pokud *fAddRef* je `AddRef` PRAVDA, je volána k zvýšení počtu odkazů pro zapouzdřený ukazatel rozhraní. Pokud *fAddRef* je `_com_ptr_t` FALSE, tento objekt převezme vlastnictví `AddRef`ukazatele nezpracované rozhraní bez volání . `Release`je volána k snížení počtu odkazů pro dříve zapouzdřený ukazatel.

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)
