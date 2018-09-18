---
title: once_flag – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/17/2018
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
ms.openlocfilehash: 67cfbe06461598fbd04e124629399baa63fdd5d9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104332"
---
# <a name="onceflag-structure"></a>once_flag – struktura

Představuje **struktura** , který se používá funkce šablony [call_once –](../standard-library/mutex-functions.md#call_once) zajistit, že inicializace kód je volán pouze jednou, i v případě výskytu více vláken provádění.

## <a name="syntax"></a>Syntaxe

once_flag – struktura {constexpr once_flag() noexcept;};

## <a name="remarks"></a>Poznámky

`once_flag` **Struktura** nemá výchozí konstruktor.

Objekty typu `once_flag` mohou být vytvořeny, ale nemůže být zkopírován.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vzájemně vyloučeného přístupu >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex – >](../standard-library/mutex.md)<br/>
