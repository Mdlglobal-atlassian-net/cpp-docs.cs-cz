---
title: 'Postupy: vytváření a používání instancí CComPtr a CComQIPtr'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
ms.openlocfilehash: e376eab75b9b1fb4a7a271d05fe037142f22e139
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246543"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>Postupy: vytváření a používání instancí CComPtr a CComQIPtr

V klasickém programování v systému Windows jsou knihovny často implementovány jako objekty modelu COM (nebo přesněji, jako servery COM). Mnoho součástí operačního systému Windows je implementováno jako servery COM a mnoho přispěvatelů poskytuje knihovny v tomto formuláři. Informace o základech modelu COM naleznete v tématu [Component Object Model (com)](/windows/win32/com/component-object-model--com--portal).

Když vytváříte instanci objektu Component Object Model (COM), uložte ukazatel rozhraní do inteligentního ukazatele modelu COM, který provede počítání odkazů pomocí volání `AddRef` a `Release` v destruktoru. Pokud používáte knihovnu ATL (Active Template Library) nebo knihovna Microsoft Foundation Class (MFC), pak použijte inteligentní ukazatel `CComPtr`. Pokud nepoužíváte ATL nebo MFC, pak použijte `_com_ptr_t`. Vzhledem k tomu, že není `std::unique_ptr`k dispozici žádný ekvivalent COM, použijte tyto inteligentní ukazatele pro scénáře jednoho vlastníka i více vlastníků. `CComPtr` i `ComQIPtr` podporují operace přesunu, které mají odkazy rvalue.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `CComPtr` pro vytvoření instance objektu COM a získání ukazatelů na jeho rozhraní. Všimněte si, že členská funkce `CComPtr::CoCreateInstance` slouží k vytvoření objektu COM namísto funkce Win32, která má stejný název.

[!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]

`CComPtr` a jeho příbuzní jsou součástí knihovny ATL a jsou definovány v \<Atlcomcli. h >. `_com_ptr_t` je deklarována v \<comip. h >. Kompilátor vytvoří specializace `_com_ptr_t` při generování obálkových tříd pro knihovny typů.

## <a name="example"></a>Příklad

ATL také poskytuje `CComQIPtr`, který má jednodušší syntaxi pro dotazování objektu COM k načtení dalšího rozhraní. Doporučujeme však, abyste `CComPtr`i, protože dělá vše, co `CComQIPtr` může dělat a je sémanticky spolehlivější s ukazateli nezpracovaných rozhraní modelu COM. Použijete-li pro dotazování na rozhraní `CComPtr`, je ukazatel nového rozhraní umístěn v parametru out. Pokud se volání nezdařilo, je vrácena hodnota HRESULT, což je typický vzor modelu COM. U `CComQIPtr`vrácená hodnota je ukazatel sám a v případě neúspěchu volání není k dispozici vnitřní návratová hodnota HRESULT. Následující dva řádky ukazují, jak se liší mechanismy zpracování chyb v `CComPtr` a `CComQIPtr`.

[!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]

## <a name="example"></a>Příklad

`CComPtr` poskytuje specializaci pro rozhraní IDispatch, která umožňuje ukládat ukazatele na komponenty automatizace modelu COM a vyvolat metody v rozhraní pomocí pozdní vazby. `CComDispatchDriver` je definice typu pro `CComQIPtr<IDispatch, &IIDIDispatch>`, která je implicitně převoditelná na `CComPtr<IDispatch>`. Proto pokud se některý z těchto tří názvů zobrazí v kódu, je ekvivalentní `CComPtr<IDispatch>`. Následující příklad ukazuje, jak získat ukazatel na objektový model aplikace Microsoft Word pomocí `CComPtr<IDispatch>`.

[!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]

## <a name="see-also"></a>Viz také:

[Chytré ukazatele (moderní verze jazyka C++)](../cpp/smart-pointers-modern-cpp.md)
