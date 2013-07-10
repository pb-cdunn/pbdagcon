What is pbdagcon?
=================

pbdagcon is a tool that implements DAGCon (Directed Acyclic Graph Consensus)
which is a sequence consensus algorithm based on using directed acyclic graphs
to encode multiple sequence alignment.

It uses the alignment information from blasr to align sequence reads to a
"backbone" sequence. Based on the underlying alignment directed acyclic graph
(DAG), it will be able to use the new information from the reads to find the
discrepancies between the reads and the "backbone" sequences.  A dynamic
programming process is then applied to the DAG to find the optimum sequence of
bases as the consensus.  The new consensus can be used as a new backbone
sequence to iteratively improve the consensus quality.

While the code is developed for processing PacBio(TM) raw sequence data, the
algorithm can be used for general consensus purpose. Currently, it only takes
FASTA input. For shorter read sequences, one might need to adjust the blasr
alignment parameters to get the alignment string properly.

The code and the underlying graphical data structure have been used for some
algorithm development prototyping including phasing reads, pre-assembly and a
work around to generate consensus from intermediate Celera Assembler outputs.

The initial graphical algorithm was a pure python implementation. Cython was
then use to speed it up.

Check out the example/ directory to see how to use it. 

This code is released under the assumption it will help the community to adopt
the PacBio data and make interesting science project possible and more
feasible.  It is not an official software release from the PacBio(TM) software
developing organization.



-----------------------------------------------------------------------------

<script>
(function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
})(window,document,'script','//www.google-analytics.com/analytics.js','ga');
ga('create', 'UA-13166584-17', 'github.com');
ga('send', 'pageview');
</script>