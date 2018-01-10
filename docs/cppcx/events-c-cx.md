---
title: "Události (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31c8e08a-00ad-40f9-8f7e-124864aaad58
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af74c81186591062214e2a8eb1695a2d177cfc04
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="events-ccx"></a>Události (C + +/ CX)
Windows Runtime můžou deklarovat typ (která se publikovat) události a kódem klientské ve stejné komponenty nebo v ostatních součástí mohou přihlásit k odběru události, tím, že přidružíte volat metody *obslužné rutiny událostí* k události. Více obslužných rutin událostí lze přidružit jednu událost. Pokud objekt publikování vyvolá událost, budou všechny obslužné rutiny událostí má být volána. Tímto způsobem můžete provádět třídu odběru ať vlastní akce je vhodné, když vydavatele vyvolává událost. Událost má typem delegáta, který určuje podpisu, který všechny obslužné rutiny události musí mít, aby přihlášení k odběru události.  
  
## <a name="consuming-events-in-windows-components"></a>Využívání události v součásti systému Windows  
 Mnoho součásti v prostředí Windows Runtime zpřístupnit události. Například objekt LightSensor aktivuje ReadingChanged událost, když senzoru hlásí novou hodnotu gradientu. Použijete-li objekt LightSensor v programu, můžete definovat metodu, která se má volat při ReadingChanged událost je aktivována. Metodu můžete dělat všechno na práci; Jediným požadavkem je, že jeho podpis musí odpovídat podpis delegáta, který je pro další informace o tom, jak vytvořit obslužnou rutinu události delegáta a přihlášení k odběru na událost, najdete v části [delegáti](../cppcx/delegates-c-cx.md).  
  
## <a name="creating-custom-events"></a>Vytváření vlastních událostí  
  
### <a name="declaration"></a>Deklarace  
 Je možné deklarovat událost v ref třídy nebo rozhraní a může mít veřejné, interní (veřejného a privátního), veřejné chráněný, chráněné, privátní chráněný, nebo privátní usnadnění. Po deklarování událost interně kompilátor vytvoří objekt, který zveřejňuje dvě metody přístupových objektů: Přidání a odebrání. Pokud odběru objekty registraci obslužné rutiny událostí, uloží je objekt události v kolekci. Při vyvolání události, vyvolá objekt událostí zase obslužné rutiny ve svém seznamu. Trivial událostí – jako v následujícím příkladu – má implicitní zálohování úložiště, která je také implicitní `add` a `remove` přístupových metod. Můžete také určit vlastní přistupující objekty stejným způsobem, že je možné zadat vlastní `get` a `set` přístupové objekty u vlastnosti.  Implementující třídu nelze ručně procházet seznam odběratele událostí v trivial události.  
  
 Následující příklad ukazuje, jak deklarace a aktivovat událost. Všimněte si, že událost má typem delegáta a je deklarovaná pomocí "^" symbol.  
  
 [!code-cpp[cx_events#01](../cppcx/codesnippet/CPP/cx_events/class1.h#01)]  
  
### <a name="usage"></a>Použití  
 Následující příklad ukazuje, jak používá třídu odběru `+=` operátor přihlášení k odběru události a poskytuje obslužné rutiny události má být volána, když je aktivována událost. Všimněte si, že funkce, která je k dispozici odpovídající podpisu delegáta, který je definován na straně vydavatele v `EventTest` oboru názvů.  
  
 [!code-cpp[cx_events#02](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#02)]  
  
> [!WARNING]
>  Obecně platí je lepší pro používání s názvem funkce, nikoli lambda, pro obslužnou rutinu události, pokud dávejte pozor, aby se zabránilo. cyklické odkazy. Funkci s názvem "Tento" ukazatel zaznamená slabé odkazu, zatímco lambda zaznamená silné odkazem a vytvoří cyklický odkaz. Další informace najdete v tématu [slabé odkazy a ukončování cykly (C + +/ CX)](../cppcx/weak-references-and-breaking-cycles-c-cx.md).  
  
### <a name="custom-add-and-remove-methods"></a>Vlastní přidávat a odebírat metody  
 Interně událost má metodu přidat, odebrat metoda a vyvolat metodu. Pokud kód klienta se přihlásí k události, volání metody přidat a delegáta, který se předává v se přidá do seznamu vyvolání události. Publikování třída vyvolá událost, způsobí, že má být volána metoda raise() a naopak je vyvolán každý delegát v seznamu. Odběratel samotné můžete odebrat ze seznamu delegáta, což způsobí, že události odebrat metoda k volání. Kompilátor poskytuje výchozí verze těchto metod, pokud je nedefinujete ve vašem kódu; Toto jsou známé jako trivial události. V mnoha případech je trivial událostí všechny, které je nutné.  
  
 Můžete zadat vlastní přidání, odebrání a vyvolat metody pro událost, pokud máte k provedení vlastní logiky v reakci na přidání nebo odebrání odběratelů. Například, pokud máte nákladné objekt, který je pouze požadované pro generování sestav událostí, můžete líné odložené vytváření objektu, dokud se klient přihlásí k událost odběru ve skutečnosti.  
  
 Další příklad ukazuje, jak přidat vlastní přidání, odebrání a vyvolání metody na událost:  
  
 [!code-cpp[cx_events#03](../cppcx/codesnippet/CPP/cx_events/class1.h#03)]  
  
## <a name="removing-an-event-handler-from-the-subscriber-side"></a>Odebrání obslužné rutiny události ze strany odběratele  
 Ve výjimečných případech můžete odebrat obslužné rutiny události pro událost, která dříve přihlášení k odběru. Například můžete chtít nahradit jinou obslužnou rutinu události nebo můžete chtít odstranit některé prostředky, které jsou uložené ve ho. Odebrat obslužnou rutinu, musíte uložit EventRegistrationToken vrácená `+=` operaci. Pak můžete použít `-=` operátor na tokenu k odebrání obslužné rutiny události.  Však může být původní obslužná rutina volána stále i po jejím odebrání. Proto pokud máte v úmyslu odebrat obslužnou rutinu události, vytvořte příznak člen a nastavte ji, pokud je událost odebere a pak události obslužnou rutinu, zkontrolujte příznak a vrátit okamžitě, pokud je nastaven. Další příklad ukazuje základní vzor.  
  
 [!code-cpp[cx_events#04](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#04)]  
  
### <a name="remarks"></a>Poznámky  
 Více obslužných rutin, může být přidružen stejnou událost. Zdroj události postupně volání všechny obslužné rutiny událostí ze stejného podprocesu. Pokud příjemce událostí blokuje v rámci obslužná rutina události, zablokuje zdroj události z vyvolání ostatních obslužných rutin událostí pro tuto událost.  
  
 Pořadí, ve kterém zdroj události vyvolá obslužné rutiny událostí v přijímače událostí není zaručena a volání z volání se můžou lišit.  
  
## <a name="see-also"></a>Viz také  
 [Systém typů](../cppcx/type-system-c-cx.md)   
 [Delegáti](../cppcx/delegates-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)