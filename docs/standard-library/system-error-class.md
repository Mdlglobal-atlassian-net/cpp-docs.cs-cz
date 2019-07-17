---
title: system_error – třída
ms.date: 11/04/2016
f1_keywords:
- system_error/std::system_error
helpviewer_keywords:
- system_error class
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
ms.openlocfilehash: 3f544cac1835a5a01e4d287cee1084bc56141716
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246243"
---
# <a name="systemerror-class"></a>system_error – třída

Představuje základní třídu pro všechny výjimky vyvolané nižší úrovně systému chybové zprávě.

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

Hodnota vrácená `what` ve třídě [výjimka](../standard-library/exception-class.md) je vytvořen z `_Message` a uložený objekt typu [error_code](../standard-library/error-code-class.md) (buď `code` nebo `error_code(_Errval, _Errcat)`).

Členská funkce `code` vrátí uloženou [error_code](../standard-library/error-code-class.md) objektu.
