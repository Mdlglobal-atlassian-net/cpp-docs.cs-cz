---
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IUnknown
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: 047e109e8098ed89ac89c05e434b54c91fda189a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270573"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) je základní rozhraní každého rozhraní COM.  Toto rozhraní definuje tři metody: [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)), [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), a [vydání](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release). [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) umožňuje uživateli rozhraní požádat o ukazatel na jinou část rozhraní objektu. [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) a [vydání](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) implementují rozhraní počítání odkazů.

## <a name="see-also"></a>Viz také:

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[IUnknown a Interface dědičnosti](/windows/desktop/com/iunknown-and-interface-inheritance)
