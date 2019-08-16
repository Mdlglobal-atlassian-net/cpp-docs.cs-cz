---
title: 'Postupy: Vytváření a používání instancí CComPtr a CComQIPtr'
ms.custom: how-to
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
ms.openlocfilehash: 8dd7aa903eefd533b1dd2688f3cee46ab3787e60
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498597"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>Postupy: Vytváření a používání instancí CComPtr a CComQIPtr

V klasickém programování v systému Windows jsou knihovny často implementovány jako objekty modelu COM (nebo přesněji, jako servery COM). Mnoho součástí operačního systému Windows je implementováno jako servery COM a mnoho přispěvatelů poskytuje knihovny v tomto formuláři. Informace o základech modelu COM naleznete v tématu [Component Object Model (com)](/windows/win32/com/component-object-model--com--portal).

Při vytváření instance objektu COM (Component Object Model) uložte ukazatel rozhraní do inteligentního ukazatele modelu COM, který provede počítání odkazů pomocí volání `AddRef` a `Release` v destruktoru. Pokud používáte knihovnu ATL (Active Template Library) nebo knihovna Microsoft Foundation Class (MFC), pak použijte `CComPtr` inteligentní ukazatel. Pokud nepoužíváte ATL nebo MFC, pak použijte `_com_ptr_t`. Vzhledem k `std::unique_ptr`tomu, že neexistuje žádný ekvivalent modelu COM, použijte tyto inteligentní ukazatele pro scénáře jednoho vlastníka i více vlastníků. `CComPtr` A`ComQIPtr` podporují operace přesunu, které mají odkazy rvalue.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `CComPtr` pro vytvoření instance objektu COM a získání ukazatelů na jeho rozhraní. Všimněte si, `CComPtr::CoCreateInstance` že členská funkce se používá k vytvoření objektu COM namísto funkce Win32, která má stejný název.

[!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]

`CComPtr`a jeho příbuzní jsou součástí knihovny ATL a jsou definovány v \<Atlcomcli. h >. `_com_ptr_t`je deklarována \<v comip. h >. Kompilátor vytvoří specializace `_com_ptr_t` při generování obálkových tříd pro knihovny typů.

## <a name="example"></a>Příklad

ATL také poskytuje `CComQIPtr`, což má jednodušší syntaxi pro dotazování objektu COM k načtení dalšího rozhraní. Nicméně doporučujeme `CComPtr` , protože vše, `CComQIPtr` co může dělat a je sémanticky konzistentní s ukazateli nezpracovaných rozhraní modelu COM. Použijete-li `CComPtr` k dotazování na rozhraní, je ukazatel nového rozhraní umístěn v parametru out. Pokud se volání nezdařilo, je vrácena hodnota HRESULT, což je typický vzor modelu COM. S `CComQIPtr`, návratovou hodnotou je ukazatel samotný a pokud volání není úspěšné, nelze získat k vnitřní vrácené hodnotě HRESULT. Následující dva řádky ukazují, jak se mechanismy `CComPtr` zpracování chyb a `CComQIPtr` liší.

[!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]

## <a name="example"></a>Příklad

`CComPtr`poskytuje specializaci pro rozhraní IDispatch, která umožňuje uložit ukazatele na komponenty automatizace modelu COM a vyvolat metody v rozhraní pomocí pozdní vazby. `CComDispatchDriver`je definice `CComQIPtr<IDispatch, &IIDIDispatch>`typu, která je implicitně převoditelná na `CComPtr<IDispatch>`. Proto pokud se některý z těchto tří názvů zobrazí v kódu, je ekvivalentní `CComPtr<IDispatch>`. Následující příklad ukazuje, jak získat ukazatel na objektový model aplikace Microsoft Word pomocí `CComPtr<IDispatch>`.

[!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]

## <a name="see-also"></a>Viz také:

[Chytré ukazatele (moderní verze jazyka C++)](../cpp/smart-pointers-modern-cpp.md)
