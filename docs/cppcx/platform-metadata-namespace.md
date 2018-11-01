---
title: Platform::metadata – Namespace
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata
helpviewer_keywords:
- Platform::Metadata Namespace
ms.assetid: e3e114d8-a4b0-47f0-865a-9ce9d7212e86
ms.openlocfilehash: 39a4709c8f66c4dcc2ee5185f2a1df27b0666445
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462865"
---
# <a name="platformmetadata-namespace"></a>Platform::metadata – Namespace

Tento obor názvů obsahuje atributy, které úpravy deklarací typů.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Platform {
   namespace Metadata {
}}
```

### <a name="members"></a>Členové

I když se tento obor názvů je určená pro interní použití, prohlížečích může zobrazit následující členy tohoto oboru názvů.

|Název|Poznámka|
|----------|------------|
|Atribut|Základní třídu pro atributy.|
|[Platform::Metadata::DefaultMemberAttribute – atribut](../cppcx/platform-metadata-defaultmemberattribute-attribute.md)|Určuje upřednostňovaný funkce k vyvolání mezi několik možných přetížených funkcí.|
|[Platform::metadata:: FlagsAttribute – atribut](../cppcx/platform-metadata-flagsattribute-attribute.md)příznaky|Deklaruje výčet jako výčet bitových polí.<br /><br /> Následující příklad ukazuje, jak použít `Flags` atribut výčet.<br /><br /> `[Flags] enum class MyEnumeration { enumA = 1, enumB = 2, enumC = 3}`|
|[Platform::Metadata::RuntimeClassNameAttribute](../cppcx/platform-metadata-runtimeclassname.md)|Zajišťuje, že privátní ref class má název třídy platný běhový.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Platform`

### <a name="requirements"></a>Požadavky

**Metadata:** platform.winmd

**Namespace:** Platform::metadata –

## <a name="see-also"></a>Viz také

[Platforma Namespace](platform-namespace-c-cx.md)