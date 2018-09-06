---
title: IUnknown | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IUnknown
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5903cebe5de87ab528dbcfe1769047b7b7ace3ef
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761911"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) je základní rozhraní každého rozhraní COM.  Toto rozhraní definuje tři metody: [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)), [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), a [vydání](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release). [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) umožňuje uživateli rozhraní požádat o ukazatel na jinou část rozhraní objektu. [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) a [vydání](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) implementují rozhraní počítání odkazů.

## <a name="see-also"></a>Viz také

[Úvod do modelu COM](../atl/introduction-to-com.md)   
[IUnknown a Interface dědičnosti](/windows/desktop/com/iunknown-and-interface-inheritance)

