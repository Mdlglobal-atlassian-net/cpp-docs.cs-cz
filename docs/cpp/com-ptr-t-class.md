---
title: _com_ptr_t – třída
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
ms.openlocfilehash: eeaab22ded537cbbb211a79596b8383251af3ab7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189898"
---
# <a name="_com_ptr_t-class"></a>_com_ptr_t – třída

**Specifické pro společnost Microsoft**

Objekt **_com_ptr_t** zapouzdření ukazatele rozhraní modelu COM a nazývá se ukazatel "inteligentního". Tato třída šablony spravuje přidělování a navracení prostředků prostřednictvím volání funkcí do `IUnknown`ch členských funkcí: `QueryInterface`, `AddRef`a `Release`.

Inteligentní ukazatel je obvykle odkazován definicí typedef, kterou poskytuje makro _COM_SMARTPTR_TYPEDEF. Toto makro přijímá název rozhraní a identifikátor IID a deklaruje specializaci **_com_ptr_t** s názvem rozhraní a příponou `Ptr`. Příklad:

```cpp
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
```

deklaruje `IMyInterfacePtr`specializace **_com_ptr_t** .

Sada [šablon funkce](../cpp/relational-function-templates.md), nikoli členové této třídy šablony, podporují porovnání s inteligentním ukazatelem na pravé straně operátoru porovnání.

### <a name="construction"></a>Stavbě

|||
|-|-|
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|Vytvoří objekt **_com_ptr_t** .|

### <a name="low-level-operations"></a>Operace nízké úrovně

|||
|-|-|
|[AddRef](../cpp/com-ptr-t-addref.md)|Volá `AddRef` členskou funkci `IUnknown` na ukazatel zapouzdřeného rozhraní.|
|[Attach](../cpp/com-ptr-t-attach.md)|Zapouzdřuje nezpracovaný ukazatel rozhraní tohoto typu inteligentního ukazatele.|
|[Metoda](../cpp/com-ptr-t-createinstance.md)|Vytvoří novou instanci objektu daného `CLSID` nebo `ProgID`.|
|[Detach](../cpp/com-ptr-t-detach.md)|Extrahuje a vrátí zapouzdřený ukazatel rozhraní.|
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|Připojí se k existující instanci objektu daného `CLSID` nebo `ProgID`.|
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|Vrátí zapouzdřený ukazatel rozhraní.|
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|Volá `QueryInterface` členskou funkci `IUnknown` na ukazatel zapouzdřeného rozhraní.|
|[Vydaná verze](../cpp/com-ptr-t-release.md)|Volá `Release` členskou funkci `IUnknown` na ukazatel zapouzdřeného rozhraní.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](../cpp/com-ptr-t-operator-equal.md)|Přiřadí novou hodnotu existujícímu objektu **_com_ptr_t** .|
|[Operators = =,! =, \<, >, \<=, > =](../cpp/com-ptr-t-relational-operators.md)|Porovná objekt inteligentního ukazatele na jiný inteligentní ukazatel, nezpracovaný ukazatel rozhraní nebo hodnotu NULL.|
|[Extraktory](../cpp/com-ptr-t-extractors.md)|Extrahuje zapouzdřený ukazatel rozhraní COM.|

**Specifické pro konec Microsoftu**

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<comip. h >

**Lib:** comsuppw. lib nebo comsuppwd. lib (viz [/Zc: Wchar_t (Wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , kde najdete další informace.)

## <a name="see-also"></a>Viz také

[Třídy podpory kompilátoru COM](../cpp/compiler-com-support-classes.md)
