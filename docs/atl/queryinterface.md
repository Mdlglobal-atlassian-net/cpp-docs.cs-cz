---
title: QueryInterface – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cde92ee56e51a86acbfb7e459571291bc3cae76c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="queryinterface"></a>QueryInterface –
I když jsou mechanismy, které můžete objekt express funkci poskytuje staticky (dříve, než je vytvořena instance), základní mechanismus COM se má používat **IUnknown** metodu s názvem [– QueryInterface ](http://msdn.microsoft.com/library/windows/desktop/ms682521).  
  
 Každé rozhraní je odvozený od **IUnknown**, takže každý rozhraní má implementace `QueryInterface`. Bez ohledu na to, implementace tato metoda dotazuje objekt, který používá identifikátory IID rozhraní, na kterou chce volající ukazatel. Pokud objekt podporuje rozhraní, `QueryInterface` načte ukazatel rozhraní při také volání `AddRef`. Funkce **E_NOINTERFACE** kód chyby.  
  
 Všimněte si, že musí orientují [počítání odkazů](../atl/reference-counting.md) pravidla za všech okolností. Když zavoláte **verze** na ukazatele rozhraní se sníží počet odkazů na nulu, byste neměli používat tento ukazatel znovu. Příležitostně budete muset získat slabé odkaz na objekt (to znamená, budete pravděpodobně chtít získat ukazatele na některého z rozhraní bez zvyšování počet odkazů), ale není přijatelné k tomu voláním `QueryInterface` následuje  **Verze**. Ukazatel získat tak je neplatný a by se neměla používat. To snadněji vyvstává zřejmá při [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) je definován, takže definování této makro je snadno chyby při počítání referencí hledání.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do modelu COM](../atl/introduction-to-com.md)   
 [QueryInterface –: Navigace v objektu](http://msdn.microsoft.com/library/windows/desktop/ms687230)

