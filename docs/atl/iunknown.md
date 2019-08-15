---
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: 9c9faa4cffcdc8e6840dfbbe141cb63f51155ded
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492063"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) je základní rozhraní každého jiného rozhraní com.  Toto rozhraní definuje tři metody: [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)), [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)a [release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release). [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) umožňuje uživateli rozhraní požádat o objekt pro ukazatel na jiný z jeho rozhraní. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) a [release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) implementují počítání odkazů na rozhraní.

## <a name="see-also"></a>Viz také:

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[Rozhraní IUnknown a dědičnost rozhraní](/windows/win32/com/iunknown-and-interface-inheritance)
