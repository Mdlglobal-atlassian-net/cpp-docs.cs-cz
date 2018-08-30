---
title: (ATL) pro počítání odkazů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1469bef0ef41c72e2ff5e59017088cd63f0f9c79
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194595"
---
# <a name="reference-counting"></a>Počítání odkazů
COM samotné nepokusí automaticky se odebere objekt z paměti při domnívá, že objekt je již nejsou déle používány. Programátor objekt místo toho musíte odebrat nepoužívané objektu. Programátor Určuje, zda objekt lze odebrat závislosti na počtu odkazů.  
  
 COM používá `IUnknown` metody, [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) a [vydání](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), spravovat počet odkazů rozhraní na objekt. Obecná pravidla pro volání těchto metod jsou:  
  
-   Pokaždé, když klient obdrží ukazatel rozhraní, `AddRef` musí být volána na rozhraní.  
  
-   Pokaždé, když klient úspěšně proběhlo pomocí ukazatele rozhraní, musí volat `Release`.  
  
 V jednoduché implementace každý `AddRef` přírůstky a každé volání `Release` volání dekrementuje proměnnou čítače v objektu. Po návratu počty na nulu, rozhraní již má všechny uživatele a je zdarma k odebrání samotné z paměti.  
  
 Počítání odkazů můžete implementovat také tak, aby se počítá každý odkaz na objekt (ne pro jednotlivá rozhraní). V tomto případě každý `AddRef` a `Release` volání delegáty pro centrální implementace objektu a `Release` při jeho počet odkazů dosáhne nuly, uvolní celý objekt.  
  
> [!NOTE]
>  Při `CComObject`-odvozené objekt je vytvořen pomocí **nové** operátor, počet odkazů je 0. Proto volání `AddRef` po úspěšném vytvoření se musí provádět `CComObject`-odvozenému objektu.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do modelu COM](../atl/introduction-to-com.md)   
 [Správa životnosti objektu prostřednictvím počítání odkazů](/windows/desktop/com/managing-object-lifetimes-through-reference-counting)

