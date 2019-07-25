---
title: future_error – třída
ms.date: 11/04/2016
f1_keywords:
- future/std::future_error
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
ms.openlocfilehash: ed3f9d63c45d0e185e3e1476094736d132822173
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447350"
---
# <a name="futureerror-class"></a>future_error – třída

Popisuje objekt výjimky, který může být vyvolán metodami typů, které spravují [budoucí](../standard-library/future-class.md) objekty.

## <a name="syntax"></a>Syntaxe

```cpp
class future_error : public logic_error {
public:
    future_error(error_code code);

const error_code& code() const throw();

const char *what() const throw();

};
```

## <a name="requirements"></a>Požadavky

**Hlavička:** \<budoucí >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[logic_error – třída](../standard-library/logic-error-class.md)\
[error_code – třída](../standard-library/error-code-class.md)
