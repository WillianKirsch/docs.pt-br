### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a><span data-ttu-id="f36dc-101">Rolagem de itens em uma lista simples de itens com diferentes alturas em pixels</span><span class="sxs-lookup"><span data-stu-id="f36dc-101">Item-scrolling a flat list with items of different pixel-height</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f36dc-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f36dc-102">Details</span></span>|<span data-ttu-id="f36dc-103">Quando um <xref:System.Windows.Controls.ItemsControl?displayProperty=name> exibe uma coleção usando virtualização (<code>IsVirtualizing=true</code>) e rolagem de itens (<code>ScrollUnit=Item</code>) e quando o controle rola para exibir um item cuja altura em pixels é diferente de seus vizinhos, o <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> itera em todos os itens na coleção.</span><span class="sxs-lookup"><span data-stu-id="f36dc-103">When an <xref:System.Windows.Controls.ItemsControl?displayProperty=name> displays a collection using virtualization (<code>IsVirtualizing=true</code>) and item- scrolling (<code>ScrollUnit=Item</code>), and when the control scrolls to display an item whose height in pixels differs from its neighbors, the <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> iterates over all items in the collection.</span></span> <span data-ttu-id="f36dc-104">A interface do usuário não responde durante essa iteração. Se a coleção for grande, isso poderá ser observado como um desligamento. A iteração ocorre em outras circunstâncias, mesmo nas versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f36dc-104">The UI is unresponsive during this iteration; if the collection is large, this can be perceived as a hang.The iteration occurs in other circumstances, even in previous .NET Framework releases.</span></span> <span data-ttu-id="f36dc-105">Por exemplo, isso ocorre na rolagem de pixels (<code>ScrollUnit=Pixel</code>) ao encontrar um item com uma altura de pixels diferente e na rolagem de itens de dados hierárquicos (como em um <xref:System.Windows.Controls.TreeView?displayProperty=name> ou um <xref:System.Windows.Controls.ItemsControl?displayProperty=name> com o agrupamento habilitado) ao encontrar um item com um número de itens descendentes diferentes de seus vizinhos. Para o caso em que há rolagem de itens e diferentes alturas em pixels, a iteração foi introduzida no .NET Framework 4.6.1 para corrigir bugs no layout de dados hierárquicos.</span><span class="sxs-lookup"><span data-stu-id="f36dc-105">For example, it occurs when pixel-scrolling (<code>ScrollUnit=Pixel</code>) upon encountering an item with different pixel height, and when item-scrolling hierarchical data (such as a <xref:System.Windows.Controls.TreeView?displayProperty=name> or an <xref:System.Windows.Controls.ItemsControl?displayProperty=name> with grouping enabled) upon encountering an item with a different number of descendant items than its neighbors.For the case of item-scrolling and different pixel height, the iteration was introduced in .NET Framework 4.6.1 to fix bugs in the layout of hierarchical data.</span></span>  <span data-ttu-id="f36dc-106">Ela não será necessária se os dados forem simples (sem hierarquia) e, nesse caso, ela não ocorre no .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="f36dc-106">It is not needed if the data is flat (no hierarchy), and .NET Framework 4.6.2 does not do it in that case.</span></span>|
|<span data-ttu-id="f36dc-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="f36dc-107">Suggestion</span></span>|<span data-ttu-id="f36dc-108">Se a iteração ocorrer no .NET Framework 4.6.1, mas não nas versões anteriores, ou seja, se o <xref:System.Windows.Controls.ItemsControl?displayProperty=name> for uma lista plana de rolagem de item com itens de alturas em pixels diferentes, haverá duas soluções:</span><span class="sxs-lookup"><span data-stu-id="f36dc-108">If the iteration occurs in .NET Framework 4.6.1 but not in earlier releases - that is, if the <xref:System.Windows.Controls.ItemsControl?displayProperty=name> is item- scrolling a flat list with items of different pixel height - there are two remedies:</span></span><ol><li><span data-ttu-id="f36dc-109">Instalar o .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="f36dc-109">Install .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="f36dc-110">Instalar o hotfix HR 1605 para o .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="f36dc-110">Install hotfix HR 1605 for .NET Framework 4.6.1.</span></span></li></ol>|
|<span data-ttu-id="f36dc-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="f36dc-111">Scope</span></span>|<span data-ttu-id="f36dc-112">Secundário</span><span class="sxs-lookup"><span data-stu-id="f36dc-112">Minor</span></span>|
|<span data-ttu-id="f36dc-113">Versão</span><span class="sxs-lookup"><span data-stu-id="f36dc-113">Version</span></span>|<span data-ttu-id="f36dc-114">4.6.1</span><span class="sxs-lookup"><span data-stu-id="f36dc-114">4.6.1</span></span>|
|<span data-ttu-id="f36dc-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="f36dc-115">Type</span></span>|<span data-ttu-id="f36dc-116">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="f36dc-116">Runtime</span></span>|
|<span data-ttu-id="f36dc-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="f36dc-117">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|
