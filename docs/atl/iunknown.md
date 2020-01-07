---
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: 6adfbdc59b2a63aa2f2bb39e27139ca977ba9465
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298750"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) je základní rozhraní každého jiného rozhraní com.  Toto rozhraní definuje tři metody: [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)), [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)a [release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release). [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) umožňuje uživateli rozhraní požádat o objekt pro ukazatel na jiný z jeho rozhraní. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) a [release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) implementují počítání odkazů na rozhraní.

## <a name="see-also"></a>Viz také:

[Úvod do modelu COM](../atl/introduction-to-com.md)<br/>
[Rozhraní IUnknown a dědičnost rozhraní](/windows/win32/com/iunknown-and-interface-inheritance)
