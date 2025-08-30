### Theory

<h4>Pushdown Automata (PDA)</h4>
<p>
A Pushdown Automaton (PDA) is a finite-state control augmented with a LIFO stack. 
Compared to a DFA (which has only finite memory), a PDA has <em>unbounded</em> memory via its stack, which lets it recognize all context‑free languages.
</p>
<p>PDA ≈ “finite-state machine” + “stack”.</p>

<h4>Core Components</h4>
<ul>
  <li><strong>Input tape</strong>: a read-only tape scanned left to right.</li>
  <li><strong>Finite control</strong>: the current state and transition logic.</li>
  <li><strong>Stack</strong>: unbounded height; top-only access (push/pop/replace).</li>
</ul>

<h4>Stack Operations</h4>
<ul>
  <li><strong>Push</strong>: write one or more symbols on top of the stack.</li>
  <li><strong>Pop</strong>: remove the top symbol.</li>
  <li><strong>Replace</strong>: pop the top symbol and push a (possibly empty) string of stack symbols (general form used by the transition function).</li>
</ul>

<h4>Formal Definition (corrected)</h4>
<p>
A PDA is a 7‑tuple <strong>M = (Q, Σ, Γ, δ, q<sub>0</sub>, Z<sub>0</sub>, F)</strong> where:
</p>
<ul>
  <li><strong>Q</strong>: finite set of states</li>
  <li><strong>Σ</strong>: input alphabet</li>
  <li><strong>Γ</strong>: stack alphabet</li>
  <li><strong>δ</strong>: transition function  
    <br>
    <code>δ: Q × (Σ ∪ {ε}) × Γ → 𝒫(Q × Γ*)</code>
    <br>
    Intuition: if <code>(p, γ) ∈ δ(q, a, X)</code>, then from state <code>q</code>, reading input symbol <code>a</code> (or <code>ε</code>), with <code>X</code> on top of the stack, the PDA may move to state <code>p</code> and replace <code>X</code> by the string <code>γ</code> (which may be <code>ε</code>).
  </li>
  <li><strong>q<sub>0</sub></strong> ∈ Q: initial state</li>
  <li><strong>Z<sub>0</sub></strong> ∈ Γ: initial stack symbol (bottom marker)</li>
  <li><strong>F</strong> ⊆ Q: set of accepting states</li>
</ul>

<h4>Acceptance</h4>
<ul>
  <li><strong>By final state</strong>: input is fully consumed and the current state is in <code>F</code>.</li>
  <li><strong>By empty stack</strong>: input is fully consumed and the stack is empty (besides the bottom marker, depending on convention).</li>
</ul>
<p>
These acceptance modes are equivalent in power: for any PDA using one mode, there exists an equivalent PDA using the other (possibly with minor construction changes).
</p>

<h4>Deterministic vs. Nondeterministic</h4>
<ul>
  <li><strong>NPDA</strong> (general case): <code>δ</code> may return multiple choices; used in most theoretical and tool settings.</li>
  <li><strong>DPDA</strong>: restricted so that each configuration has at most one move (no nondeterminism and no conflicting ε‑moves).</li>
</ul>

<p>
This revised theory corrects earlier inaccuracies—especially the transition function, which must map to a <em>set</em> of state/stack‑string pairs—and uses standard notation (Γ for stack alphabet, Z<sub>0</sub> for the initial stack symbol, F ⊆ Q).
</p>