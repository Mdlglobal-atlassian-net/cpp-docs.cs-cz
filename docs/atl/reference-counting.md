---
title: "(ATL) při počítání referencí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9bef78ba6047305ccb20e5740ae03535ca2c366b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="reference-counting"></a>Počítání odkazů
COM, samotné nezkusí automaticky k odebrání objektu z paměti, když se domnívá, že objekt je již používána. Objekt programátorů místo toho musíte odebrat nepoužité objektu. Programátorů Určuje, zda objekt lze odebrat podle počet odkazů.  
  
 Používá COM **IUnknown** metody, [addref –](http://msdn.microsoft.com/library/windows/desktop/ms691379) a [verze](http://msdn.microsoft.com/library/windows/desktop/ms682317), ke správě počet odkazů rozhraní na objekt. Obecná pravidla pro volání těchto metod jsou:  
  
-   Vždy, když klient obdrží ukazatele rozhraní, `AddRef` musí být voláno na rozhraní.  
  
-   Vždy, když klient dokončí, pomocí rozhraní ukazatele, musí volat **verze**.  
  
 Jednoduché implementace každý `AddRef` volání přírůstcích a každý **verze** volání snižuje proměnnou čítače v objektu. Pokud počet vrátí na nulu, rozhraní již má všechny uživatele a může sám sebe odebrat z paměti.  
  
 Počítání odkazů můžete implementovat také tak, aby se počítá každý odkaz na objekt (ne pro jednotlivé rozhraní). V takovém případě každé `AddRef` a **verze** volání delegáti centrální implementaci na objekt, a **verze** celý objekt uvolní, když jeho počet odkazů hodnota nula.  
  
> [!NOTE]
>  Při `CComObject`-odvozené objekt se vytvoří pomocí **nové** operátor, počet odkazů je 0. Proto volání `AddRef` musí být provedeny po úspěšném vytvoření `CComObject`-odvozené objektu.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do modelu COM](../atl/introduction-to-com.md)   
 [Správa životnosti objektu prostřednictvím počítání odkazů](http://msdn.microsoft.com/library/windows/desktop/ms687260)

