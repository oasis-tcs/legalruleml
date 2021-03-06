<h1>Use Case #1</h1>

This use case presents LegalRuleML serializations of <a href="https://academic.oup.com/logcom/article-abstract/27/8/2471/3098296?redirectedFrom=fulltext">reified Input/Output 
logic</a> formulae from <a href="https://link.springer.com/article/10.1007/s10849-019-09309-z?shared-article-renderer">the DAPRECO knowledge base (D-KB)</a>. The D-KB formalizes the norms in the <a href="https://eur-lex.europa.eu/eli/reg/2016/679/oj">General Data Protection Regulation (GDPR)</a> into 966 reified Input/Output logic formulae. The full D-KB is available <a href="https://raw.githubusercontent.com/dapreco/daprecokb/master/gdpr/rioKB_GDPR.xml">at this link</a>.

Two examples from the D-KB are selected for this use case. They are briefly described below, while the full LegalRuleML files may be downloaded from <a href="https://github.com/oasis-tcs/legalruleml/blob/master/usecases/files/Examples%20from%20the%20D-KB.zip">this link</a>; the files contain further comments and clarifications. Further examples are presented in <a href="https://link.springer.com/article/10.1007/s10849-019-09309-z?shared-article-renderer">[Robaldo et al., 2019]</a>.

<h2>Example 1</h2>

Example 1 formalizes art. 12(7), of the GDPR. The example includes two main if-then rules in reified Input/Output logic, formalizing each the statements:

<ol>
   <li>"<i>If the controller provides information to the data subject, he is permitted to attach an icon</i>"</li>
   <li>"<i>If the controller provides information to the data subject and attach an electronic icon, then he is obliged to make the icon machine-readable</i>"</li>
</ol>

Statement (1) is formalized by the following rule in RuleML. The rule states that whenever there is a communication between the controller and the data subject, the controller is permitted to attach (predicate "AttachTo") an icon. Note that the if-then rule do not contain deontic operators. In Input/Output logics, deontic reasoning is implemented in an external level (see <a href="https://link.springer.com/chapter/10.1007/978-94-017-0395-6_12">[Makinson and van der Torre, 2000]</a>). The rule below is then a standard first-order logic implication which is tagged as permission via the LegalRuleML tag "lrml:Context". See <a href="https://link.springer.com/article/10.1007/s10849-019-09309-z?shared-article-renderer">[Robaldo et al., 2019]</a> for more details.

      <ruleml:Rule closure="universal">
        <ruleml:if>
          <ruleml:Exists>
            <ruleml:Var key=":a1">a1</ruleml:Var>
            <ruleml:Var key=":ep">ep</ruleml:Var>
            <ruleml:Var key=":edp">edp</ruleml:Var>
            <ruleml:Var key=":w">w</ruleml:Var>
            <ruleml:Var key=":z">z</ruleml:Var>
            <ruleml:Var key=":x">x</ruleml:Var>
            <ruleml:Var key=":i">i</ruleml:Var>
            <ruleml:And>
              <ruleml:Atom>
                <ruleml:Rel iri="rioOnto:RexistAtTime" />
                <ruleml:Var keyref=":a1" />
                <ruleml:Var key=":t1">t1</ruleml:Var>
              </ruleml:Atom>
              <ruleml:Atom keyref=":A854">
                <ruleml:Rel iri="rioOnto:and" />
                <ruleml:Var keyref=":a1" />
                <ruleml:Var keyref=":ep" />
                <ruleml:Var key=":en">en</ruleml:Var>
                <ruleml:Var keyref=":edp" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:DataSubject" />
                <ruleml:Var keyref=":w" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:PersonalData" />
                <ruleml:Var keyref=":z" />
                <ruleml:Var keyref=":w" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Controller" />
                <ruleml:Var key=":y">y</ruleml:Var>
                <ruleml:Var keyref=":z" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Processor" />
                <ruleml:Var keyref=":x" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A855">
                <ruleml:Rel iri="prOnto:nominates" />
                <ruleml:Var keyref=":edp" />
                <ruleml:Var keyref=":y" />
                <ruleml:Var keyref=":x" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A856">
                <ruleml:Rel iri="prOnto:PersonalDataProcessing" />
                <ruleml:Var keyref=":ep" />
                <ruleml:Var keyref=":x" />
                <ruleml:Var keyref=":z" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A857">
                <ruleml:Rel iri="prOnto:Communicate" />
                <ruleml:Var keyref=":en" />
                <ruleml:Var keyref=":y" />
                <ruleml:Var keyref=":w" />
                <ruleml:Var keyref=":i" />
              </ruleml:Atom>
            </ruleml:And>
          </ruleml:Exists>
        </ruleml:if>
        <ruleml:then>
          <ruleml:Exists>
            <ruleml:Var key=":eat">eat</ruleml:Var>
            <ruleml:Var key=":ic">ic</ruleml:Var>
            <ruleml:And>
              <ruleml:Atom>
                <ruleml:Rel iri="rioOnto:RexistAtTime" />
                <ruleml:Var keyref=":eat" />
                <ruleml:Var keyref=":t1" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A858">
                <ruleml:Rel iri="dapreco:AttachTo" />
                <ruleml:Var keyref=":eat" />
                <ruleml:Var keyref=":y" />
                <ruleml:Var keyref=":ic" />
                <ruleml:Var keyref=":en" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="dapreco:Icon" />
                <ruleml:Var keyref=":ic" />
              </ruleml:Atom>
            </ruleml:And>
          </ruleml:Exists>
        </ruleml:then>
      </ruleml:Rule>

Statement (2) is formalized by the following rule in RuleML, which states that whenever an icon is attached to a communication between the controller and the data subject, then the icon must be obligatorily in machine-readable form. This rule is tagged as obligation, again via the LegalRuleML tag "lrml:Context".

      <ruleml:Rule closure="universal">
        <ruleml:if>
          <ruleml:Exists>
            <ruleml:Var key=":a1">a1</ruleml:Var>
            <ruleml:Var key=":ep">ep</ruleml:Var>
            <ruleml:Var key=":en">en</ruleml:Var>
            <ruleml:Var key=":eat">eat</ruleml:Var>
            <ruleml:Var key=":el">el</ruleml:Var>
            <ruleml:Var key=":edp">edp</ruleml:Var>
            <ruleml:Var key=":w">w</ruleml:Var>
            <ruleml:Var key=":z">z</ruleml:Var>
            <ruleml:Var key=":y">y</ruleml:Var>
            <ruleml:Var key=":x">x</ruleml:Var>
            <ruleml:Var key=":i">i</ruleml:Var>
            <ruleml:And>
              <ruleml:Atom>
                <ruleml:Rel iri="rioOnto:RexistAtTime" />
                <ruleml:Var keyref=":a1" />
                <ruleml:Var key=":t1">t1</ruleml:Var>
              </ruleml:Atom>
              <ruleml:Atom keyref=":A859">
                <ruleml:Rel iri="rioOnto:and" />
                <ruleml:Var keyref=":a1" />
                <ruleml:Var keyref=":ep" />
                <ruleml:Var keyref=":en" />
                <ruleml:Var keyref=":eat" />
                <ruleml:Var keyref=":el" />
                <ruleml:Var keyref=":edp" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:DataSubject" />
                <ruleml:Var keyref=":w" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:PersonalData" />
                <ruleml:Var keyref=":z" />
                <ruleml:Var keyref=":w" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Controller" />
                <ruleml:Var keyref=":y" />
                <ruleml:Var keyref=":z" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Processor" />
                <ruleml:Var keyref=":x" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A860">
                <ruleml:Rel iri="prOnto:nominates" />
                <ruleml:Var keyref=":edp" />
                <ruleml:Var keyref=":y" />
                <ruleml:Var keyref=":x" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A861">
                <ruleml:Rel iri="prOnto:PersonalDataProcessing" />
                <ruleml:Var keyref=":ep" />
                <ruleml:Var keyref=":x" />
                <ruleml:Var keyref=":z" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A862">
                <ruleml:Rel iri="prOnto:Communicate" />
                <ruleml:Var keyref=":en" />
                <ruleml:Var keyref=":y" />
                <ruleml:Var keyref=":w" />
                <ruleml:Var keyref=":i" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A863">
                <ruleml:Rel iri="dapreco:AttachTo" />
                <ruleml:Var keyref=":eat" />
                <ruleml:Var keyref=":y" />
                <ruleml:Var key=":ic">ic</ruleml:Var>
                <ruleml:Var keyref=":en" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="dapreco:Icon" />
                <ruleml:Var keyref=":ic" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A864">
                <ruleml:Rel iri="dapreco:electronicForm" />
                <ruleml:Var keyref=":el" />
                <ruleml:Var keyref=":ic" />
              </ruleml:Atom>
            </ruleml:And>
          </ruleml:Exists>
        </ruleml:if>
        <ruleml:then>
          <ruleml:Exists>
            <ruleml:Var key=":emr">emr</ruleml:Var>
            <ruleml:And>
              <ruleml:Atom>
                <ruleml:Rel iri="rioOnto:RexistAtTime" />
                <ruleml:Var keyref=":emr" />
                <ruleml:Var keyref=":t1" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A865">
                <ruleml:Rel iri="dapreco:machineReadableness" />
                <ruleml:Var keyref=":emr" />
                <ruleml:Var keyref=":ic" />
              </ruleml:Atom>
            </ruleml:And>
          </ruleml:Exists>
        </ruleml:then>
      </ruleml:Rule>


<h2>Example 2</h2>

Example 2 formalizes artt. 5(1)(a), 6(1)(a), 8(1) of the GDPR. The example includes the following if-then rules in reified Input/Output logic, formalizing each the statements:

<ol>
   <li>"<i>The controller is obliged to implement measures that cause the lawfulness, the fairness, and the transparency of the processing of personal data</i>"</li>
   <li>"<i>If the data subject has given consent to the processing, then the processing is lawful</i>"</li>
   <li>"<i>The minimal age for giving consent is 16, unless there is a specific exception within the Member State (Member States are allowed to lower the minimal age for giving consent to the data processing, but not lower than 13)</i>"</li>
   <li>"<i>If the age of the data subject is below the minimal age for giving consent, then rule (2) is not valid</i>"</li>
   <li>"<i>If the age of the data subject is below the minimal age for giving consent and the holder of his parental responsibility has given consent to the processing, then the processing is lawful</i>"</li>
</ol>

Statement (1) is formalized by the following rule in RuleML, stating that whenever there is a data processing ":ep", then the controller is obliged to implement measures ":em" that cause the processing to be lawful, fair, and transparent (facts ":el", ":ef", and ":et").

      <ruleml:Rule closure="universal">
        <ruleml:if>
          <ruleml:Exists>
            <ruleml:Var key=":a1">a1</ruleml:Var>
            <ruleml:Var key=":edp">edp</ruleml:Var>
            <ruleml:Var key=":z">z</ruleml:Var>
            <ruleml:Var key=":x">x</ruleml:Var>
            <ruleml:And>
              <ruleml:Atom>
                <ruleml:Rel iri="rioOnto:RexistAtTime" />
                <ruleml:Var keyref=":a1" />
                <ruleml:Var key=":t1">t1</ruleml:Var>
              </ruleml:Atom>
              <ruleml:Atom keyref=":A1">
                <ruleml:Rel iri="rioOnto:and" />
                <ruleml:Var keyref=":a1" />
                <ruleml:Var key=":ep">ep</ruleml:Var>
                <ruleml:Var keyref=":edp" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:DataSubject" />
                <ruleml:Var key=":w">w</ruleml:Var>
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:PersonalData" />
                <ruleml:Var keyref=":z" />
                <ruleml:Var keyref=":w" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Controller" />
                <ruleml:Var key=":y">y</ruleml:Var>
                <ruleml:Var keyref=":z" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Processor" />
                <ruleml:Var keyref=":x" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A2">
                <ruleml:Rel iri="prOnto:nominates" />
                <ruleml:Var keyref=":edp" />
                <ruleml:Var keyref=":y" />
                <ruleml:Var keyref=":x" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A3">
                <ruleml:Rel iri="prOnto:PersonalDataProcessing" />
                <ruleml:Var keyref=":ep" />
                <ruleml:Var keyref=":x" />
                <ruleml:Var keyref=":z" />
              </ruleml:Atom>
            </ruleml:And>
          </ruleml:Exists>
        </ruleml:if>
        <ruleml:then>
          <ruleml:Exists>
            <ruleml:Var key=":a2">a2</ruleml:Var>
            <ruleml:Var key=":t2">t2</ruleml:Var>
            <ruleml:Var key=":ei">ei</ruleml:Var>
            <ruleml:Var key=":ec1">ec1</ruleml:Var>
            <ruleml:Var key=":ec2">ec2</ruleml:Var>
            <ruleml:Var key=":ec3">ec3</ruleml:Var>
            <ruleml:Var key=":ed">ed</ruleml:Var>
            <ruleml:Var key=":em">em</ruleml:Var>
            <ruleml:Var key=":el">el</ruleml:Var>
            <ruleml:Var key=":ef">ef</ruleml:Var>
            <ruleml:Var key=":et">et</ruleml:Var>
            <ruleml:And>
              <ruleml:Atom>
                <ruleml:Rel iri="rioOnto:RexistAtTime" />
                <ruleml:Var keyref=":a2" />
                <ruleml:Var keyref=":t2" />
              </ruleml:Atom>
              <ruleml:Atom>
              <ruleml:After>
                <ruleml:Var keyref=":t2" />
                <ruleml:Var keyref=":t1" />
              </ruleml:After>
              </ruleml:Atom>
              <ruleml:Atom keyref=":A4">
                <ruleml:Rel iri="rioOnto:and" />
                <ruleml:Var keyref=":a2" />
                <ruleml:Var keyref=":ei" />
                <ruleml:Var keyref=":ec1" />
                <ruleml:Var keyref=":ec2" />
                <ruleml:Var keyref=":ec3" />
                <ruleml:Var keyref=":ed" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Measure" />
                <ruleml:Var keyref=":em" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A5">
                <ruleml:Rel iri="dapreco:Implement" />
                <ruleml:Var keyref=":ei" />
                <ruleml:Var keyref=":y" />
                <ruleml:Var keyref=":em" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A6">
                <ruleml:Rel iri="rioOnto:cause" />
                <ruleml:Var keyref=":ec1" />
                <ruleml:Var keyref=":em" />
                <ruleml:Var keyref=":el" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A7">
                <ruleml:Rel iri="prOnto:lawfulness" />
                <ruleml:Var keyref=":el" />
                <ruleml:Var keyref=":ep" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A8">
                <ruleml:Rel iri="rioOnto:cause" />
                <ruleml:Var keyref=":ec2" />
                <ruleml:Var keyref=":em" />
                <ruleml:Var keyref=":ef" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A9">
                <ruleml:Rel iri="prOnto:fairness" />
                <ruleml:Var keyref=":ef" />
                <ruleml:Var keyref=":ep" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A10">
                <ruleml:Rel iri="rioOnto:cause" />
                <ruleml:Var keyref=":ec3" />
                <ruleml:Var keyref=":em" />
                <ruleml:Var keyref=":et" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A11">
                <ruleml:Rel iri="prOnto:transparency" />
                <ruleml:Var keyref=":et" />
                <ruleml:Var keyref=":ep" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="dapreco:RelatedTo" />
                <ruleml:Var keyref=":ep" />
                <ruleml:Var keyref=":w" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A12">
                <ruleml:Rel iri="dapreco:Describe" />
                <ruleml:Var keyref=":ed" />
                <ruleml:Var keyref=":y" />
                <ruleml:Var keyref=":ei" />
              </ruleml:Atom>
            </ruleml:And>
          </ruleml:Exists>
        </ruleml:then>
      </ruleml:Rule>

Statement (2) is a first-order entailment stating that if the data subject has given consent to the data processing, then the data processing is lawful, unless a specific exception on the age of the data subject (denoted by the predicate “rioOnto:exceptionCha2Art8Par1”). By default, this exception is false via negation-as-failure (RuleML tag "ruleml:Naf"):

      <ruleml:Rule closure="universal">
        <ruleml:if>
          <ruleml:Exists>
            <ruleml:Var key=":a1">a1</ruleml:Var>
            <ruleml:Var key=":t1">t1</ruleml:Var>
            <ruleml:Var key=":ehc">ehc</ruleml:Var>
            <ruleml:Var key=":eau">eau</ruleml:Var>
            <ruleml:Var key=":edp">edp</ruleml:Var>
            <ruleml:Var key=":w">w</ruleml:Var>
            <ruleml:Var key=":z">z</ruleml:Var>
            <ruleml:Var key=":y">y</ruleml:Var>
            <ruleml:Var key=":x">x</ruleml:Var>
            <ruleml:Var key=":epu">epu</ruleml:Var>
            <ruleml:Var key=":c">c</ruleml:Var>
            <ruleml:And>
              <ruleml:Atom>
                <ruleml:Rel iri="rioOnto:RexistAtTime" />
                <ruleml:Var keyref=":a1" />
                <ruleml:Var keyref=":t1" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A160">
                <ruleml:Rel iri="rioOnto:and" />
                <ruleml:Var keyref=":a1" />
                <ruleml:Var key=":ep">ep</ruleml:Var>
                <ruleml:Var keyref=":ehc" />
                <ruleml:Var keyref=":eau" />
                <ruleml:Var keyref=":edp" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:DataSubject" />
                <ruleml:Var keyref=":w" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:PersonalData" />
                <ruleml:Var keyref=":z" />
                <ruleml:Var keyref=":w" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Controller" />
                <ruleml:Var keyref=":y" />
                <ruleml:Var keyref=":z" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Processor" />
                <ruleml:Var keyref=":x" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A161">
                <ruleml:Rel iri="prOnto:nominates" />
                <ruleml:Var keyref=":edp" />
                <ruleml:Var keyref=":y" />
                <ruleml:Var keyref=":x" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A162">
                <ruleml:Rel iri="prOnto:PersonalDataProcessing" />
                <ruleml:Var keyref=":ep" />
                <ruleml:Var keyref=":x" />
                <ruleml:Var keyref=":z" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Purpose" />
                <ruleml:Var keyref=":epu" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:isBasedOn" />
                <ruleml:Var keyref=":ep" />
                <ruleml:Var keyref=":epu" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Consent" />
                <ruleml:Var keyref=":c" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A163">
                <ruleml:Rel iri="dapreco:GiveConsent" />
                <ruleml:Var keyref=":ehc" />
                <ruleml:Var keyref=":w" />
                <ruleml:Var keyref=":c" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A164">
                <ruleml:Rel iri="dapreco:AuthorizedBy" />
                <ruleml:Var keyref=":eau" />
                <ruleml:Var keyref=":epu" />
                <ruleml:Var keyref=":c" />
              </ruleml:Atom>
              <ruleml:Naf>
                <ruleml:Atom>
                  <ruleml:Rel iri="rioOnto:exceptionCha2Art8Par1" />
                  <ruleml:Var keyref=":ep" />
                </ruleml:Atom>
              </ruleml:Naf>
            </ruleml:And>
          </ruleml:Exists>
        </ruleml:if>
        <ruleml:then>
          <ruleml:And>
            <ruleml:Atom>
              <ruleml:Rel iri="prOnto:lawfulness" />
              <ruleml:Var keyref=":ep" />
            </ruleml:Atom>
          </ruleml:And>
        </ruleml:then>
      </ruleml:Rule>

Statement (3) is a first-order entailment stating that the minimal age for giving consent to the processing, denoted by a first-order function "minAgeForConsent" that takes in input an event of data processing ":ep" and returns an integer, is 16, unless the exception "exceptionMinAgeForConsent" holds. The latter is false by default, but if the Member State of the data subject lower the minimal age for giving consent to the processing, then the predicate "exceptionMinAgeForConsent" becomes true.

      <ruleml:Rule closure="universal">
        <ruleml:if>
          <ruleml:Exists>
            <ruleml:Var key=":x">x</ruleml:Var>
            <ruleml:Var key=":z">z</ruleml:Var>
            <ruleml:Var key=":w">w</ruleml:Var>
            <ruleml:Naf>
              <ruleml:Atom>
                <ruleml:Rel iri="rioOnto:exceptionMinAgeForConsent" />
                <ruleml:Var key=":ep">ep</ruleml:Var>
              </ruleml:Atom>
            </ruleml:Naf>
            <ruleml:Atom keyref=":A3">
              <ruleml:Rel iri="prOnto:PersonalDataProcessing" />
              <ruleml:Var keyref=":ep" />
              <ruleml:Var keyref=":x" />
              <ruleml:Var keyref=":z" />
            </ruleml:Atom>
            <ruleml:Atom>
              <ruleml:Rel iri="prOnto:DataSubject" />
              <ruleml:Var keyref=":w" />
            </ruleml:Atom>
            <ruleml:Atom>
              <ruleml:Rel iri="prOnto:PersonalData" />
              <ruleml:Var keyref=":z" />
              <ruleml:Var keyref=":w" />
            </ruleml:Atom>
            <ruleml:Atom>
              <ruleml:Rel iri="prOnto:Processor" />
              <ruleml:Var keyref=":x" />
            </ruleml:Atom>
          </ruleml:Exists>
        </ruleml:if>
        <ruleml:then>
          <ruleml:Atom>
            <ruleml:Rel iri="swrlb:equal"/>
            <ruleml:Expr>
              <ruleml:Fun iri="dapreco:minAgeForConsent" />
              <ruleml:Var keyref=":ep" />
            </ruleml:Expr>
            <ruleml:Ind>16</ruleml:Ind>
          </ruleml:Atom>
        </ruleml:then>
      </ruleml:Rule>

Statement (4) is a first-order entailment stating that if the age of the data subject, given by a function "ageOf" that takes a data subject and returns an integer, is lower than the minimal age to give consent, then exception "exceptionCha2Art8Par1" holds. This blocks the rule associated with statement (2), as explained above.

      <ruleml:Rule closure="universal">
        <ruleml:if>
          <ruleml:Exists>
            <ruleml:Var key=":a1">a1</ruleml:Var>
            <ruleml:Var key=":t1">t1</ruleml:Var>
            <ruleml:Var key=":edp">edp</ruleml:Var>
            <ruleml:Var key=":w">w</ruleml:Var>
            <ruleml:Var key=":z">z</ruleml:Var>
            <ruleml:Var key=":y">y</ruleml:Var>
            <ruleml:Var key=":x">x</ruleml:Var>
            <ruleml:And>
              <ruleml:Atom>
                <ruleml:Rel iri="rioOnto:RexistAtTime" />
                <ruleml:Var keyref=":a1" />
                <ruleml:Var keyref=":t1" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A318">
                <ruleml:Rel iri="rioOnto:and" />
                <ruleml:Var keyref=":a1" />
                <ruleml:Var key=":ep">ep</ruleml:Var>
                <ruleml:Var keyref=":edp" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:DataSubject" />
                <ruleml:Var keyref=":w" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:PersonalData" />
                <ruleml:Var keyref=":z" />
                <ruleml:Var keyref=":w" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Controller" />
                <ruleml:Var keyref=":y" />
                <ruleml:Var keyref=":z" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Processor" />
                <ruleml:Var keyref=":x" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A319">
                <ruleml:Rel iri="prOnto:nominates" />
                <ruleml:Var keyref=":edp" />
                <ruleml:Var keyref=":y" />
                <ruleml:Var keyref=":x" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A320">
                <ruleml:Rel iri="prOnto:PersonalDataProcessing" />
                <ruleml:Var keyref=":ep" />
                <ruleml:Var keyref=":x" />
                <ruleml:Var keyref=":z" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="swrlb:lessThanOrEqual" />
                <ruleml:Expr>
                  <ruleml:Fun iri="dapreco:ageOf" />
                  <ruleml:Var keyref=":w" />
                </ruleml:Expr>
                <ruleml:Expr>
                  <ruleml:Fun iri="dapreco:minAgeForConsent" />
                  <ruleml:Var keyref=":ep" />
                </ruleml:Expr>
              </ruleml:Atom>
            </ruleml:And>
          </ruleml:Exists>
        </ruleml:if>
        <ruleml:then>
          <ruleml:Atom>
            <ruleml:Rel iri="rioOnto:exceptionCha2Art8Par1" />
            <ruleml:Var keyref=":ep" />
          </ruleml:Atom>
        </ruleml:then>
      </ruleml:Rule>

Statement (5) is a first-order entailment similar to statement (2) above: if the age of the data subject is lower than the minimal age to give consent and the holder of his parental responsibility has given consent to the data processing, then the data processing is lawful. Contrary to statement (2), the GDPR does not specify any exception for statement (5).

      <ruleml:Rule closure="universal">
        <ruleml:if>
          <ruleml:Exists>
            <ruleml:Var key=":a1">a1</ruleml:Var>
            <ruleml:Var key=":t1">t1</ruleml:Var>
            <ruleml:Var key=":ehc">ehc</ruleml:Var>
            <ruleml:Var key=":eau">eau</ruleml:Var>
            <ruleml:Var key=":edp">edp</ruleml:Var>
            <ruleml:Var key=":w">w</ruleml:Var>
            <ruleml:Var key=":z">z</ruleml:Var>
            <ruleml:Var key=":y">y</ruleml:Var>
            <ruleml:Var key=":x">x</ruleml:Var>
            <ruleml:Var key=":epu">epu</ruleml:Var>
            <ruleml:Var key=":c">c</ruleml:Var>
            <ruleml:And>
              <ruleml:Atom>
                <ruleml:Rel iri="rioOnto:RexistAtTime" />
                <ruleml:Var keyref=":a1" />
                <ruleml:Var keyref=":t1" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A321">
                <ruleml:Rel iri="rioOnto:and" />
                <ruleml:Var keyref=":a1" />
                <ruleml:Var key=":ep">ep</ruleml:Var>
                <ruleml:Var keyref=":ehc" />
                <ruleml:Var keyref=":eau" />
                <ruleml:Var keyref=":edp" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:DataSubject" />
                <ruleml:Var keyref=":w" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:PersonalData" />
                <ruleml:Var keyref=":z" />
                <ruleml:Var keyref=":w" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Controller" />
                <ruleml:Var keyref=":y" />
                <ruleml:Var keyref=":z" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Processor" />
                <ruleml:Var keyref=":x" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A322">
                <ruleml:Rel iri="prOnto:nominates" />
                <ruleml:Var keyref=":edp" />
                <ruleml:Var keyref=":y" />
                <ruleml:Var keyref=":x" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A323">
                <ruleml:Rel iri="prOnto:PersonalDataProcessing" />
                <ruleml:Var keyref=":ep" />
                <ruleml:Var keyref=":x" />
                <ruleml:Var keyref=":z" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Purpose" />
                <ruleml:Var keyref=":epu" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:isBasedOn" />
                <ruleml:Var keyref=":ep" />
                <ruleml:Var keyref=":epu" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="prOnto:Consent" />
                <ruleml:Var keyref=":c" />
              </ruleml:Atom>
              <ruleml:Atom>
                <ruleml:Rel iri="swrlb:lessThanOrEqual" />
                <ruleml:Expr>
                  <ruleml:Fun iri="dapreco:ageOf" />
                  <ruleml:Var keyref=":w" />
                </ruleml:Expr>
                <ruleml:Expr>
                  <ruleml:Fun iri="dapreco:minAgeForConsent" />
                  <ruleml:Var keyref=":c" />
                </ruleml:Expr>
              </ruleml:Atom>
              <ruleml:Atom keyref=":A324">
                <ruleml:Rel iri="dapreco:GiveConsent" />
                <ruleml:Var keyref=":ehc" />
                <ruleml:Expr>
                  <ruleml:Fun iri="dapreco:HolderOfPR" />
                  <ruleml:Var keyref=":w" />
                </ruleml:Expr>
                <ruleml:Var keyref=":c" />
              </ruleml:Atom>
              <ruleml:Atom keyref=":A325">
                <ruleml:Rel iri="dapreco:AuthorizedBy" />
                <ruleml:Var keyref=":eau" />
                <ruleml:Var keyref=":epu" />
                <ruleml:Var keyref=":c" />
              </ruleml:Atom>
            </ruleml:And>
          </ruleml:Exists>
        </ruleml:if>
        <ruleml:then>
          <ruleml:Atom>
            <ruleml:Rel iri="prOnto:lawfulness" />
            <ruleml:Var keyref=":ep" />
          </ruleml:Atom>
        </ruleml:then>
      </ruleml:Rule>
