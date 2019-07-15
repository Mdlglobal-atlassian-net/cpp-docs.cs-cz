---
title: Události (C++/CX)
ms.date: 07/15/2019
ms.assetid: 31c8e08a-00ad-40f9-8f7e-124864aaad58
ms.openlocfilehash: d0a3ab01628487dcca081eb300470cbd1bf3bb83
ms.sourcegitcommit: fd466f2e14ad001f52f3dbe54f46d77be10f2d7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "67894457"
---
# <a name="events-ccx"></a>Události (C++/CX)

Windows Runtime lze deklarovat typ (který je, publikování) události a kódem klientské pod stejnou komponentou nebo v jiných součástech mohou přihlásit k odběru těchto událostí tím, že přidružíte volání metody *obslužné rutiny událostí* s událostí. Více obslužných rutin událostí lze přidružit jednu událost. Při publikování objektu vyvolá událost, dojde k vyvolání všech obslužných rutin událostí. Tímto způsobem můžete provádět odběratelská třídy jakýkoli vlastní akce je vhodné, když vydavatele vyvolává událost. Událost má typ delegáta, který určuje signatura, kterou musí mít všechny obslužné rutiny událostí k události registrovat.

## <a name="consuming-events-in-windows-components"></a>Spotřebovávajících událostí ve Windows komponenty

Mnoho komponent v prostředí Windows Runtime vystavit události. Například objekt LightSensor aktivuje událost ReadingChanged při senzor sestavy novou hodnotu gradientu. Při použití objektu LightSensor ve svém programu, můžete definovat metodu, která bude volána po ReadingChanged událost se aktivuje. Metodu můžete dělat cokoliv, co chcete udělat; Jediným požadavkem je, že jeho podpis musí odpovídat signatuře delegáta, která je vyvolána. Další informace o tom, jak vytvořit obslužnou rutinu události delegáta a přihlášení k odběru události najdete v tématu [delegáti](../cppcx/delegates-c-cx.md).

## <a name="creating-custom-events"></a>Vytváření vlastních událostí

### <a name="declaration"></a>Deklarace

Je možné deklarovat událost třídy ref class nebo rozhraní a může mít interní public (veřejné nebo soukromé), chráněné veřejné, privátní, chráněné přístupnost protected nebo private. Při deklaraci události interně kompilátor vytvoří objekt, který poskytuje dva přístupové metody: Přidání a odebrání. Když odběratelská objekty zaregistrujte obslužné rutiny událostí, uloží je objekt události v kolekci. Když se aktivuje událost, vyvolá objekt události zase všechny obslužné rutiny ve svém seznamu. Triviální události – například v následujícím příkladu – má implicitní záložní úložiště, který je také implicitní `add` a `remove` přístupové metody. Můžete také určit vlastní přístupové objekty stejným způsobem, že můžete zadat vlastní `get` a `set` přistupující objekty na vlastnost.  Implementující třída nelze ručně cyklicky procházet události seznam předplatitelů v jednoduché události.

Následující příklad ukazuje, jak deklarovat a vyvolat událost. Všimněte si, že událost má typ delegáta a je deklarovaná příkazem using "^" symbol.

[!code-cpp[cx_events#01](../cppcx/codesnippet/CPP/cx_events/class1.h#01)]

### <a name="usage"></a>Použití

Následující příklad ukazuje, jak používá třídu odběratelská `+=` operátor k události registrovat a poskytuje obslužné rutiny události má být volána, když se aktivuje událost. Všimněte si, že funkce, která je k dispozici odpovídá signatuře delegáta, který je definován na straně vydavatele v `EventTest` oboru názvů.

[!code-cpp[cx_events#02](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#02)]

> [!WARNING]
> Obecně je vhodnější použít pojmenované funkce namísto výrazu lambda pro obslužnou rutinu události nezvolíte velmi pečlivě, aby se zabránilo cyklické odkazy. Pojmenované funkce zachycuje ukazatel "Tento" podle nestálý odkaz, že výraz lambda zachytí silné odkazem a vytváří cyklický odkaz. Další informace najdete v tématu [slabé odkazy a cykly zásadní (C++/CX)](../cppcx/weak-references-and-breaking-cycles-c-cx.md).

### <a name="custom-add-and-remove-methods"></a>Vlastní přidání a odebrání metody

Interně událost nemá metodu přidat, odebrat metodu a vyvolat metodu. Pokud klientský kód přihlásí k události, volá metodu add a delegáta, který je předán se přidá do seznamu vyvolání události. Publikování třída vyvolá událost, způsobí, že metoda raise() volat a zase vyvolání všem delegátům v seznamu. Odběratel samotné odebrat ze seznamu delegáta, což způsobí, že události odebírací metoda k volání. Kompilátor poskytuje výchozí verze těchto metod, pokud nejsou jejich definování v kódu; Toto jsou známé jako jednoduché události. V mnoha případech je jednoduché události vše, co vyžaduje.

Můžete zadat vlastní přidání, odebrání a vyvolat metody pro událost, pokud je nutné provést vlastní logiku v reakci na přidávání nebo odebírání předplatitelů. Například, pokud máte nákladný objekt, který je jen požadované události vytváření sestav, můžete laxně odložit vytvoření objektu, dokud klient ve skutečnosti se přihlásí k odběru události.

Následující příklad ukazuje, jak přidat vlastní přidání, odebrání a vyvolání metody na událost:

[!code-cpp[cx_events#03](../cppcx/codesnippet/CPP/cx_events/class1.h#03)]

## <a name="removing-an-event-handler-from-the-subscriber-side"></a>Odebírá obslužnou rutinu události ze strany odběratele

V některých výjimečných případech můžete chtít odebrat obslužnou rutinu události pro událost, která jste dříve nepřihlásili k odběru. Například můžete chtít nahradit jinou obslužnou rutinu události nebo můžete chtít odstranit některé prostředky, které jsou uloženy tímto plánem. Chcete-li odebrat obslužnou rutinu, musí ukládat EventRegistrationToken, která je vrácena z `+=` operace. Pak můžete použít `-=` operátor na token, který se má odebrat obslužnou rutinu události.  Původní obslužná rutina však mohou být volány stále, i když se odebere. Proto pokud máte v úmyslu odebrat obslužnou rutinu události, vytvořte příznak, který člen a nastavte ji Pokud událost odebere a pak v případě obslužnou rutinu, zkontrolujte příznak a výsledky okamžitě, pokud je nastavena. Následující příklad zobrazuje základní vzor.

[!code-cpp[cx_events#04](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#04)]

### <a name="remarks"></a>Poznámky

Více obslužných rutin, může být spojen s stejné události. Zdroj události postupně volá všechny obslužné rutiny událostí ze stejného podprocesu. Pokud přijímače událostí blokuje v rámci metody obslužné rutiny událostí, blokuje zdroj události z volání jiné obslužné rutiny událostí pro tuto událost.

Pořadí, ve kterém zdroj události vyvolá obslužných rutin událostí v příjemci událostí není zaručeno a volání z volání se může lišit.

## <a name="see-also"></a>Viz také:

[Systém typů](../cppcx/type-system-c-cx.md)<br/>
[Delegáti](../cppcx/delegates-c-cx.md)<br/>
[Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
