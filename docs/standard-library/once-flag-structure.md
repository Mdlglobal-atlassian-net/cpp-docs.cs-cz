---
title: once_flag – struktura
ms.date: 09/17/2018
f1_keywords:
- mutex/std::once_flag
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
ms.openlocfilehash: fb85bd48f9b1ac10ec2fefbc6738aae777f67bcf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455196"
---
# <a name="onceflag-structure"></a>once_flag – struktura

Představuje **strukturu** , která se používá se šablonou funkce [call_once](../standard-library/mutex-functions.md#call_once) , aby se zajistilo, že inicializační kód se volá jenom jednou, a to i v případě, že je v přítomnosti více podprocesů provádění.

## <a name="syntax"></a>Syntaxe

once_flag struktury {constexpr once_flag (), s výjimkou;};

## <a name="remarks"></a>Poznámky

Struktura má pouze výchozí konstruktor.  `once_flag`

Objekty typu `once_flag` lze vytvořit, ale nelze je zkopírovat.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> mutex

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
