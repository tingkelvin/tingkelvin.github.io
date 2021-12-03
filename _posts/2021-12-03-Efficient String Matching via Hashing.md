---
layout: post
title: Attack Graph in Cyber Security
description: Attack Graph decrtibes the squence of events in cyber attack.

---
**Direct Graph**

In large scale of computer network, user authentication is crucial in the process that keeps unauthorized users from gaining access to sensitive information. User authenication indicates a directional relationships between computers and users. Therefore, this user authenication relationship can be modelled by directed graphs. These directed graphs can be broken down into many Person's Authentication Subgraphs(PAS) was defined by Ken, Liebrock & Neil to model user authenication and behvrious.

<div class="row mt-3">
    <div class="col-md mt-3 mt-md-0"></div>
    <div class="col-md mt-3 mt-md-0">
        {% responsive_image path: assets/img/attackgraph/attackgraph.png class: "img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-md mt-3 mt-md-0"></div>
</div>
<div class="caption">
    Fig. 1 - A simple directed graph shows that a user u can log into computer c1 which has access to computers from c2 to c3.
</div>

**Definition**

A path is defined as a squenece of arcs from
vertice $$ v_{1}$$ to vertex $$v_{n}$$.

$$ P_{u}(v_{1}, v_{n}) = (v_{1}, v_{2}),...,(v_{n-1}, v_{n})\ s.t.\ (v_{j}, v_{j+1}) \in A_{u}, j=1,...,n-1.$$

A path distance $$d(x,y)$$ is defined as the shortest path from vertex $$x$$ to vertex $$y$$.

A Diameter is defined as the maximum distance $$ d=(x,y) $$ between any two vertices within $$G_{u}$$.

$$D_{u} = max\ d(x,y)\ s.t. x,y \in V_{u} \wedge P_{u}(x,y) \neq \emptyset$$

The first time the arc $$(x,y)$$ was observed is defined as $$t_{first}(x,y)$$.

The last time the arc $$(x,y)$$ was observed is defined as $$t_{last}(x,y)$$

$$ \overrightarrow{p_{u}}(v_{1}, v_{n}) = (v_{1}, v_{2}),...,(v_{n-1}, v_{n})\ s.t.$$

$$t_{last}(v_{j}, v_{j+1}) \geq max(t_{first}(v_{1}, v_{2}),...,t_{first}(v_{j}, v_{j+1}))$$

The maximum time-constrained distance is defined as,

$$ \overrightarrow{D_{u}} = max\ \overrightarrow{d} (x,y) s.t. x,y \in V_{u}  \wedge P_{u}(x,y) \neq \emptyset$$

This can illustrated using the following example,

<div class="row mt-3">
    <div class="col-md mt-3 mt-md-0"></div>
    <div class="col-md mt-3 mt-md-0">
        {% responsive_image path: assets/img/attackgraph/attackpath.png class: "img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-md mt-3 mt-md-0"></div>
</div>
<div class="caption">
    Fig. 2 - The longest non-time-constrained path with a length of 3 (from v1 to v4). The longest time-contrained path with a length of 2 (from v1 to v3) because the last time from v3 to v4 is smaller than first time from v2 to v3. That means v4 was logged from v3 before v3 was logged from v2 implies they are disconnected.
</div>

The set of vertices $$O_{u}$$ as outstars where each vertex has an outdegree greater than 1 and out degree is greater than outdegree.

$$O_{u} = \{ v \in V_{u}\ |\ deg^{+}(v) > 1 \wedge deg^{-}(v) \geq deg^{+}(v) \}$$

The set of vertices $$I_{u}$$ as instars where each vertex has an outdegree greater than 1 and out degree is greater than outdegree.

$$I_{u} = \{ v \in V_{u}\ |\ deg^{-}(v) > 1 \wedge deg^{+}(v) \geq deg^{-}(v) \}$$

Vertices that both indegree and outdegree of zero is defined as isolated verices Z_{u}.

$$Z_{u} = \{ v \in V_{u}\ |\ deg^{-}(v) = 0 \wedge deg^{+}(v) = 0\}$$

Time-constrained transit vertices $$\overrightarrow{T}_{u}$$, where each member vertex v has at least one arc proceeding from a parent vertex and one arc succeeding to a child vertex.

$$Z_{u} = \{ v \in V_{u}\ |\ deg^{-}(v) = 0 \wedge deg^{+}(v) = 0\}$$


