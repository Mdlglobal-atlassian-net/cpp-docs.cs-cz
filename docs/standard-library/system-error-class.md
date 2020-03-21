---
title: system_error – třída
ms.date: 11/04/2016
f1_keywords:
- system_error/std::system_error
helpviewer_keywords:
- system_error class
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
ms.openlocfilehash: 7a18d2f9f229a62a539be072870e38a990677636
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076364"
---
# <a name="system_error-class"></a>system_error – třída

Představuje základní třídu pro všechny výjimky vyvolané k hlášení systémové chyby nízké úrovně.

## <a name="syntax"></a>Syntaxe

```cpp
class system_error : public runtime_error {
    explicit system_error(error_code _Errcode, const string& _Message = "");
    system_error(error_code _Errcode, const char *_Message);
    system_error(error_code::value_type _Errval, const error_category& _Errcat, const string& _Message);
    system_error(error_code::value_type _Errval, const error_category& _Errcat, const char *_Message);

    const error_code& code() const throw();
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>Poznámky

Hodnota vrácená `what` v [výjimce](../standard-library/exception-class.md) třídy je vytvořena z `_Message` a uloženého objektu typu [error_code](../standard-library/error-code-class.md) (buď `code`, nebo `error_code(_Errval, _Errcat)`).

Členská funkce `code` vrátí uložený objekt [error_code](../standard-library/error-code-class.md) .
