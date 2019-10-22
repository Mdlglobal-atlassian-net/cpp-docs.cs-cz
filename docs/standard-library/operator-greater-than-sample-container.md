---
title: operátor &gt; (&gt; &lt;sample kontejneru)
ms.date: 11/04/2016
f1_keywords:
- std::operator>
- operator>
- std::>
- '>'
helpviewer_keywords:
- '> operator, comparing specific objects'
- operator >
ms.assetid: 49bd417a-3305-4ffa-9884-39d3904ed87d
ms.openlocfilehash: 80bcc6b81ec7d6771895f711d61a507f057eae2a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689191"
---
# <a name="operatorgt-ltsample-containergt"></a>operátor &gt; (&gt; &lt;sample kontejneru)

> [!NOTE]
> Toto téma se nachází v dokumentaci C++ společnosti Microsoft jako nefunkční příklad kontejnerů použitých ve C++ standardní knihovně. Další informace najdete v tématu [ C++ standardní kontejnery knihovny](../standard-library/stl-containers.md).

**Operátor přetížení >** pro porovnání dvou objektů [kontejneru](../standard-library/sample-container-class.md)šablon třídy.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
bool operator*gt;(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Návratová hodnota

Vrátí `right < left`.

## <a name="see-also"></a>Viz také:

[> kontejneru \<sample](../standard-library/sample-container.md)
