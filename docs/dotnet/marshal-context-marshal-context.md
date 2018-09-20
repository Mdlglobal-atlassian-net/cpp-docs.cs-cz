---
title: marshal_context::marshal_context | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- marshal_context::marshal_context
- msclr.interop.marshal_context.marshal_context
- marshal_context.marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 5f08c895-60b0-4f72-97ff-7ae37c68e853
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 02f238a8d9b9d484073794b9a75888325d95107b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399441"
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::marshal_context

Vytvoří `marshal_context` objektu, který chcete použít pro převod dat mezi spravovaným a nativním datové typy.

## <a name="syntax"></a>Syntaxe

```
marshal_context();
```

## <a name="remarks"></a>Poznámky

Některé převodů dat vyžadují zařazování kontextu. Zobrazit [Overview of Marshaling in C++](../dotnet/overview-of-marshaling-in-cpp.md) Další informace o překlady, které vyžadují kontextu a které zařazování soubor musí být součástí vaší aplikace.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md).

## <a name="requirements"></a>Požadavky

**Soubor hlaviček:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, nebo \<msclr\marshal_atl.h >

**Namespace:** msclr::interop

## <a name="see-also"></a>Viz také

[Přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)<br/>
[marshal_context Class](../dotnet/marshal-context-class.md)