---
title: C2592 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2592
dev_langs:
- C++
helpviewer_keywords:
- C2592
ms.assetid: 833a4d7b-66ef-4d4c-ae83-a533c2b0eb07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5d999056d718d9c7aad93d08a99895caebbef539
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229810"
---
# <a name="compiler-error-c2592"></a>C2592 chyby kompilátoru
'class': 'base_class_2' je zděděn z 'base_class_1' a nejde ho znovu zadaný  
  
 Zadávat lze pouze základní třídy, které nedědí z jiné základní třídy. V tomto případě pouze `base_class_1` je potřeba ve specifikaci `class` protože `base_class_1` již dědí `base_class_2`.