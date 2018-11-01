---
title: marshal_context::~marshal_context
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- marshal_context::~marshal_context
- msclr.interop.marshal_context.~marshal_context
- marshal_context.~marshal_context
- msclr::interop::marshal_context::~marshal_context
- ~marshal_context
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 34c41b38-4c33-4f61-b74e-831ac46b4ab5
ms.openlocfilehash: 3bf16ab2dde4047fb845cd700821d097f733a4d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528216"
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::~marshal_context

Odstraní `marshal_context` objektu.

## <a name="syntax"></a>Syntaxe

```
~marshal_context();
```

## <a name="remarks"></a>Poznámky

Některé převodů dat vyžadují zařazování kontextu. Zobrazit [Overview of Marshaling in C++](../dotnet/overview-of-marshaling-in-cpp.md) Další informace o překlady, které vyžadují kontextu a které zařazování soubor musí být součástí vaší aplikace.

Odstranění `marshal_context` objekt zruší platnost dat převedených pomocí daného kontextu. Pokud chcete zachovat data po `marshal_context` objekt je zničen, musíte ručně zkopírovat data do proměnné, která se zachová.

## <a name="requirements"></a>Požadavky

**Soubor hlaviček:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, nebo \<msclr\marshal_atl.h >

**Namespace:** msclr::interop

## <a name="see-also"></a>Viz také

[Přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)<br/>
[marshal_context Class](../dotnet/marshal-context-class.md)