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
ms.openlocfilehash: d4f842b799a81179fa1a612e652aae391ca3375d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435659"
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
