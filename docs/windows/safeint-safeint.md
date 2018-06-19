---
title: SafeInt::SafeInt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeInt::SafeInt
- SafeInt
- SafeInt.SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class, constructor
ms.assetid: 39e6f632-a396-40e6-9ece-cc3d4c5a78ef
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c7154349105c1953ad314b7928e7be8385179c42
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888744"
---
# <a name="safeintsafeint"></a>SafeInt::SafeInt
Vytvoří `SafeInt` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SafeInt() throw  
  
SafeInt (  
   const T& i  
) throw ()  
  
SafeInt (  
   bool b  
) throw ()  
  
template <typename U>  
SafeInt (  
   const SafeInt <U, E>& u  
)  
  
I template <typename U>  
SafeInt (  
   const U& i  
)  
```  
  
#### <a name="parameters"></a>Parametry  
 [v] `i`  
 Hodnota pro nové `SafeInt` objektu. Toto musí být parametr typu T nebo U, v závislosti na konstruktoru.  
  
 [v] `b`  
 Logickou hodnotu pro nové `SafeInt` objektu.  
  
 [v] `u`  
 A `SafeInt` z typu U. Nové `SafeInt` objektu bude mít stejnou hodnotu jako `u`, ale bude typu T.  
  
 U  
 Typ dat uložených v `SafeInt`. To může být typu logická hodnota, znak nebo celé číslo. Pokud je typ integer, může být podepsané nebo nepodepsané a být v rozsahu 8 až 64 bitů.  
  
## <a name="remarks"></a>Poznámky  
 Další informace o typech šablon `T` a `E`, najdete v části [SafeInt – třída](../windows/safeint-class.md).  
  
 Vstupní parametr pro konstruktor, `i` nebo `u`, musí být typu logická hodnota, znak nebo celé číslo. Pokud je jiný typ parametru, `SafeInt` třídy volání [static_assert](../cpp/static-assert.md) udávajících Neplatný vstupní parametr.  
  
 Konstruktory, které používají typ šablony `U` automaticky převést vstupní parametr typu zadaném pomocí `T`. `SafeInt` Třída převádí data bez ke ztrátě dat. Oznámí na obslužnou rutinu chyby `E` Pokud nemůže převést data na typ `T` bez ztráty dat.  
  
 Pokud vytvoříte `SafeInt` z logického parametru, je nutné inicializovat hodnota okamžitě. Nelze vytvořit `SafeInt` pomocí kódu `SafeInt<bool> sb;`. Tím se vygeneruje chybu kompilace.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** safeint.h  
  
 **Namespace:** msl::utilities  
  
## <a name="see-also"></a>Viz také  
 [SafeInt – knihovna](../windows/safeint-library.md)   
 [SafeInt – třída](../windows/safeint-class.md)   
 [SafeIntException – třída](../windows/safeintexception-class.md)