---
title: Události (C++/CX)
description: Jak použít C++/CX k vytváření a používání obslužných rutin událostí v prostředí Windows Runtime.
ms.date: 02/03/2020
ms.assetid: 31c8e08a-00ad-40f9-8f7e-124864aaad58
ms.openlocfilehash: 45f9a7bc17d9a695613ce551dae796b2cd2e0e6f
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972203"
---
# <a name="events-ccx"></a>Události (C++/CX)

Prostředí Windows Runtime typ může deklarovat (to znamená, publikovat) události a kód klienta ve stejné komponentě nebo v jiných součástech se může přihlásit k odběru těchto událostí přidružením metod nazývaných *obslužné rutiny události* s událostí. K jedné události může být přidruženo více obslužných rutin událostí. Když publikovaný objekt vyvolá událost, způsobí vyvolání všech obslužných rutin událostí. Tímto způsobem může třída pro odběr provádět jakékoli vlastní akce, když Vydavatel událost vyvolá. Událost má typ delegáta, který určuje podpis, který musí mít všechny obslužné rutiny událostí, aby se mohl přihlásit k odběru události.

## <a name="consuming-events-in-windows-components"></a>Spotřebovávání událostí v součástech systému Windows

Mnoho komponent v prostředí Windows Runtime zpřístupňuje události. Například objekt LightSensor aktivuje událost ReadingChanged, když senzor ohlásí novou hodnotu luminescence. Použijete-li v programu objekt LightSensor, můžete definovat metodu, která bude volána při vyvolání události ReadingChanged. Metoda může dělat vše, co chcete udělat; Jediným požadavkem je, aby se jeho signatura shodovala s signaturou delegáta, který je vyvolán. Další informace o tom, jak vytvořit obslužnou rutinu události delegáta a přihlásit se k odběru události, naleznete v tématu [Delegáti](../cppcx/delegates-c-cx.md).

## <a name="creating-custom-events"></a>Vytváření vlastních událostí

### <a name="declaration"></a>Deklarace

Můžete deklarovat událost v referenční třídě nebo rozhraní a může mít veřejné, interní (veřejné nebo soukromé), veřejné chráněné, chráněné, soukromé chráněné nebo privátní přístupnost. Při deklaraci události interně kompilátor vytvoří objekt, který zveřejňuje dvě metody přístupového objektu: Přidat a odebrat. Při odběru obslužných rutin událostí v registraci objektů, objekt události je uloží do kolekce. Při vyvolání události vyvolá objekt události všechny obslužné rutiny v jejím seznamu. Triviální událost – podobně jako v následujícím příkladu – má implicitní záložní úložiště a také implicitní `add` a přístupové metody `remove`. Můžete také zadat vlastní přistupující objekty tak, aby bylo možné zadat vlastní `get` a přístupové objekty `set` na vlastnost.  Implementující třída nemůže manuálně přepínat seznam odběratelů událostí v triviální události.

Následující příklad ukazuje, jak deklarovat a vyvolat událost. Všimněte si, že událost má typ delegáta a je deklarována pomocí symbolu "^".

[!code-cpp[cx_events#01](../cppcx/codesnippet/CPP/cx_events/class1.h#01)]

### <a name="usage"></a>Použití

Následující příklad ukazuje, jak třída pro odběr používá operátor `+=` k přihlášení k odběru události a poskytnutí obslužné rutiny události, která má být vyvolána při vyvolání události. Všimněte si, že zadaná funkce odpovídá signatuře delegáta, který je definován na straně vydavatele v oboru názvů `EventTest`.

[!code-cpp[cx_events#02](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#02)]

> [!WARNING]
> Obecně je vhodnější použít pojmenovanou funkci, nikoli lambda, pro obslužnou rutinu události, pokud nebudete mít velkou péči, abyste se vyhnuli cyklickým odkazům. Pojmenovaná funkce zachycuje "This" ukazatel na slabý odkaz, zatímco lambda ho zachytí silným odkazem a vytvoří cyklický odkaz. Další informace najdete v tématu [slabé odkazy a cykly přerušeníC++(/CX)](../cppcx/weak-references-and-breaking-cycles-c-cx.md).

### <a name="custom-add-and-remove-methods"></a>Vlastní metody Add a Remove

Interně událost obsahuje metodu Add, metodu Remove a metodu vyvolání. Když se klientský kód přihlašuje k odběru události, zavolá se metoda Add a předaný delegát se přidá do seznamu vyvolání události. Třída publikování vyvolá událost, způsobí, že metoda Invoke () bude volána a každý delegát v seznamu je vyvolán. Předplatitel může ze seznamu delegátů odebrat sebe sama, což způsobí, že metoda Remove události bude volána. Kompilátor poskytuje výchozí verze těchto metod, pokud je nedefinujete v kódu; Ty se nazývají triviální události. V mnoha případech je triviální událost povinná.

Můžete zadat vlastní metody přidání, odebrání a vyvolání pro událost, pokud je třeba provést vlastní logiku v reakci na přidání nebo odebrání předplatitelů. Například pokud máte nákladný objekt, který je vyžadován pouze pro oznamování událostí, můžete laxně vytvářená vytvořit objekt, dokud se klient ve skutečnosti nepřipojí k odběru události.

Další příklad ukazuje, jak přidat vlastní metody přidání, odebrání a vyvolání pro událost:

[!code-cpp[cx_events#03](../cppcx/codesnippet/CPP/cx_events/class1.h#03)]

## <a name="removing-an-event-handler-from-the-subscriber-side"></a>Odebrání obslužné rutiny události ze strany odběratele

V některých vzácných případech může být vhodné odebrat obslužnou rutinu události pro událost, kterou jste předtím přihlásili k odběru. Například můžete chtít nahradit jinou obslužnou rutinu události nebo můžete chtít odstranit některé prostředky, které jsou v něm uloženy. Chcete-li odebrat obslužnou rutinu, je nutné uložit EventRegistrationToken, který je vrácen z operace `+=`. Pak můžete použít operátor `-=` na tokenu k odebrání obslužné rutiny události.  Původní obslužná rutina však může být stále vyvolána i po jejím odebrání. Například konflikt časování může nastat, když zdroj události získá seznam obslužných rutin a začne je volat. Pokud dojde k odebrání obslužné rutiny události, seznam se stane neaktuálním. Takže pokud máte v úmyslu odebrat obslužnou rutinu události, vytvořte příznak členu. Nastavte jej, pokud je událost odebrána, a poté v obslužné rutině události zaškrtněte příznak a ihned vraťte, pokud je nastavena. Následující příklad ukazuje základní vzor.

[!code-cpp[cx_events#04](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#04)]

### <a name="remarks"></a>Poznámky

Ke stejné události může být přidruženo více obslužných rutin. Zdroj události postupně volá do všech obslužných rutin událostí ze stejného vlákna. Pokud přijímač události v rámci metody obslužné rutiny události zablokuje zdroj události pro vyvolání jiných obslužných rutin událostí pro tuto událost.

Pořadí, ve kterém zdroj události vyvolává obslužné rutiny událostí, není zaručeno a může se lišit od volání volání.

## <a name="see-also"></a>Viz také:

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Delegáti](../cppcx/delegates-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
