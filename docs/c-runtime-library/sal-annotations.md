---
title: SAL – poznámky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __z annotation
- ref annotation
- _opt annotation
- __checkreturn annotatioin
- __deref_opt annotation
- deref_opt annotation
- __deref annotation
- __in annotation
- annotations [C++]
- z annotation
- _inout annotation
- __ref annotation
- full annotation
- _in annotation
- _ref annotation
- __out annotation
- _ecount annotation
- SAL annotations
- __opt annotation
- inout annotation
- in annotation
- _CA_SHOULD_CHECK_RETURN
- __bcount annotation
- _full annotation
- _bcount annotation
- deref annotation
- part annotation
- _out annotation
- __nz annotation
- __part annotation
- opt annotation
- __full annotation
- _nz annotation
- _z annotation
- out annotation
- __ecount annotation
- __inout annotation
- SAL annotations, _CA_SHOULD_CHECK_RETURN
- _deref_opt annotation
- _deref annotation
- nz annotation
- _part annotation
- ecount annotation
- bcount annotation
ms.assetid: 81893638-010c-41a0-9cb3-666fe360f3e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2eb935285c8c90c238baf59cd11a1232fa33d895
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409381"
---
# <a name="sal-annotations"></a>Poznámky SAL
Pokud si projdete soubory hlaviček knihovny, můžete si povšimnout některé neobvyklou poznámky, například `_In_z` a `_Out_z_cap_(_Size)`. Toto jsou příklady jazyka Microsoft zdrojového kódu poznámky (SAL), která poskytuje sada poznámky popisují, jak funkce používá jeho parametry, například předpoklady, které provádí o nich a záruky, které provádí na dokončení. Soubor hlaviček \<sal.h > definuje poznámky.  
  
 Další informace o použití poznámek SAL v sadě Visual Studio najdete v tématu [použití poznámek SAL k snížení závad kódu C/C++](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects).  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)