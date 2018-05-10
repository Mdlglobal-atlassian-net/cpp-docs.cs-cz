---
title: once_flag – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::once_flag
dev_langs:
- C++
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8a8d28f19e32988bfa179642a87e880413bb0ff
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="onceflag-structure"></a>once_flag – struktura

Představuje `struct` používané funkce šablony [call_once –](../standard-library/mutex-functions.md#call_once) zajistit, že inicializace kód je volat pouze jednou, ani za přítomnosti více vláken provádění.

## <a name="syntax"></a>Syntaxe

once_flag – struktura {constexpr once_flag() noexcept; once_flag(const once_flag&); once_flag – & operátor =(const once_flag&);};

## <a name="remarks"></a>Poznámky

`once_flag` `struct` Má výchozí konstruktor.

Objekty typu `once_flag` mohou být vytvořeny, ale nelze kopírovat.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<mutex >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex >](../standard-library/mutex.md)<br/>
