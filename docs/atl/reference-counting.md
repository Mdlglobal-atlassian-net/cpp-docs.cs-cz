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
ms.openlocfilehash: 8e0ce8b2cc412c576b0eded9662d8e70b34cf2ec
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850810"
---
# <a name="reference-counting"></a>Počítání odkazů
COM samotné nepokusí automaticky se odebere objekt z paměti při domnívá, že objekt je již nejsou déle používány. Programátor objekt místo toho musíte odebrat nepoužívané objektu. Programátor Určuje, zda objekt lze odebrat závislosti na počtu odkazů.  
  
 COM používá `IUnknown` metody, [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) a [vydání](http://msdn.microsoft.com/library/windows/desktop/ms682317), spravovat počet odkazů rozhraní na objekt. Obecná pravidla pro volání těchto metod jsou:  
  
-   Pokaždé, když klient obdrží ukazatel rozhraní, `AddRef` musí být volána na rozhraní.  
  
-   Pokaždé, když klient úspěšně proběhlo pomocí ukazatele rozhraní, musí volat `Release`.  
  
 V jednoduché implementace každý `AddRef` přírůstky a každé volání `Release` volání dekrementuje proměnnou čítače v objektu. Po návratu počty na nulu, rozhraní již má všechny uživatele a je zdarma k odebrání samotné z paměti.  
  
 Počítání odkazů můžete implementovat také tak, aby se počítá každý odkaz na objekt (ne pro jednotlivá rozhraní). V tomto případě každý `AddRef` a `Release` volání delegáty pro centrální implementace objektu a `Release` při jeho počet odkazů dosáhne nuly, uvolní celý objekt.  
  
> [!NOTE]
>  Při `CComObject`-odvozené objekt je vytvořen pomocí **nové** operátor, počet odkazů je 0. Proto volání `AddRef` po úspěšném vytvoření se musí provádět `CComObject`-odvozenému objektu.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do modelu COM](../atl/introduction-to-com.md)   
 [Správa životnosti objektu prostřednictvím počítání odkazů](http://msdn.microsoft.com/library/windows/desktop/ms687260)

