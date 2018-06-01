---
title: '&lt;Poznámky&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- remarks
- <remarks>
dev_langs:
- C++
helpviewer_keywords:
- <remarks> C++ XML tag
- remarks C++ XML tag
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 380a2c27a761154e59826259d3e1e682ae7fbd87
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33334464"
---
# <a name="ltremarksgt-visual-c"></a>&lt;Poznámky&gt; (Visual C++)
\<Poznámky > Značka se používá k přidání informací o typu, doplňující informace zadaným [ \<souhrnné >](../ide/summary-visual-cpp.md). Tyto informace se zobrazí v [Prohlížeč objektů](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470) a v sestavě webové komentář kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>Parametry  
 `description`  
 Popis člena.  
  
## <a name="remarks"></a>Poznámky  
 Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
  
```  
// xml_remarks_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_remarks_tag.dll  
  
using namespace System;  
  
/// <summary>  
/// You may have some primary information about this class.  
/// </summary>  
/// <remarks>  
/// You may have some additional information about this class.  
/// </remarks>  
public ref class MyClass {};  
```  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace XML](../ide/xml-documentation-visual-cpp.md)