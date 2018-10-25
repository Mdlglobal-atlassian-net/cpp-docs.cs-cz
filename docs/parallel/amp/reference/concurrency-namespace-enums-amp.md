---
title: Výčty oboru názvů Concurrency (AMP) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
dev_langs:
- C++
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58d70b995642eaca3dbefd75383e6d6bf06f2c62
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082428"
---
# <a name="concurrency-namespace-enums-amp"></a>Výčty oboru názvů Concurrency (AMP)

|||
|-|-|
|[access_type – výčet](#access_type)|[queuing_mode – výčet](#queuing_mode)|

##  <a name="access_type"></a>  access_type – výčet

Typ výčtu se používá k označení různých typů přístupu k datům.

```
enum access_type;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`access_type_auto`|Automaticky vybrat nejlepší `access_type` pro akcelerátor.|
|`access_type_none`|Vyhrazená. Rozdělení je přístupné u akcelerátoru a ne v procesoru jen.|
|`access_type_read`|Sdílet. Rozdělení je přístupné u akcelerátoru a číst v procesoru.|
|`access_type_read_write`|Sdílet. Rozdělení je přístupné u akcelerátoru a umožňuje zapisovat v procesoru.|
|`access_type_write`|Sdílet. Rozdělení je přístupné u akcelerátoru a číst i zapisovat v procesoru.|

##  <a name="queuing_mode"></a>  queuing_mode – výčet

Určuje režimy zařazování do fronty, které jsou podporovány v akcelerátoru.

```
enum queuing_mode;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`queuing_mode_immediate`|Režim zařazování do fronty, která určuje, že všechny příkazy, například [parallel_for_each – funkce (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each), odesílají do odpovídajících zařízení akcelerátoru ihned po jejich vrácení volajícímu.|
|`queuing_mode_automatic`|Režim zařazování do fronty, která určuje, že se příkazy zařazeny příkazové fronty odpovídající [accelerator_view](accelerator-view-class.md) objektu. Příkazy jsou odesílány na zařízení při [accelerator_view::flush](accelerator-view-class.md#flush) je volána.|

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
