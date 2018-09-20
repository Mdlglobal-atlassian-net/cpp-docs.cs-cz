---
title: marshal_context – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fc3399ee088a0430ca857c3e421742ee484d337a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413312"
---
# <a name="marshalcontext-class"></a>marshal_context – třída

Tato třída převádí data mezi nativními a spravovanými prostředími.

## <a name="syntax"></a>Syntaxe

```
class marshal_context
```

## <a name="remarks"></a>Poznámky

Použití `marshal_context` třídu pro převodů dat, které vyžadují kontextu. Zobrazit [Overview of Marshaling in C++](../dotnet/overview-of-marshaling-in-cpp.md) Další informace o převody, které vyžadují kontextu a zařazování souborů, které se mají být zahrnuty. Výsledek zařazování při použití kontextu je platný pouze dokud `marshal_context` objekt zničen. Pro zachování vašich výsledek, je nutné zkopírovat data.

Stejné `marshal_context` lze použít pro více dat převody. Opětovné použití kontextu tímto způsobem nebude mít vliv na výsledky z předchozího volání zařazování.

## <a name="requirements"></a>Požadavky

**Soubor hlaviček:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, nebo \<msclr\marshal_atl.h >

**Namespace:** msclr::interop

## <a name="see-also"></a>Viz také

[Přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)