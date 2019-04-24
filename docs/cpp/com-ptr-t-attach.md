---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 4b4b7a21d12cc645c486dd93d555510c1e716563
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154887"
---
# <a name="comptrtattach"></a>_com_ptr_t::Attach

**Microsoft Specific**

Zapouzdřuje nezpracovaný ukazatel rozhraní tohoto inteligentního ukazatele typu.

## <a name="syntax"></a>Syntaxe

```
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>Parametry

*pInterface*<br/>
Nezpracovaný ukazatel rozhraní.

*fAddRef*<br/>
Pokud je hodnota TRUE, pak `AddRef` je volána. Pokud má hodnotu FALSE, `_com_ptr_t` objekt převezme vlastnictví nezpracovaného ukazatele rozhraní bez volání `AddRef`.

## <a name="remarks"></a>Poznámky

- **Připojení (***pInterface***)** `AddRef` není volána. To je předáno vlastnictví rozhraní `_com_ptr_t` objektu. `Release` nazývá se sníží počet odkazů na dříve zapouzdřený ukazatel.

- **Připojení (***pInterface* **,***fAddRef***)** Pokud *fAddRef* má hodnotu TRUE, `AddRef`nazývá se zvýší počet odkazů pro zapouzdřený ukazatel rozhraní. Pokud *fAddRef* má hodnotu FALSE, to `_com_ptr_t` objekt převezme vlastnictví nezpracovaného ukazatele rozhraní bez volání `AddRef`. `Release` nazývá se sníží počet odkazů na dříve zapouzdřený ukazatel.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)