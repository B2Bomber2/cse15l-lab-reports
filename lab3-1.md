# Lab 3 Report: Bugs and Commands (Week 5)
Ferrari Guan A17917695

## Introduction

<br />
Lab 3 encompassed testing and debugging; command line manipulation, especially for finding files; and Bash scripting. The commands ```find```, ```less```, and ```grep``` were introduced during the lab session. 
<br />

## Part 1: Bugs
<br />

The following shows the process of debugging a method in Java by utilizing the JUnit framework. 
The following buggy method is being tested. 
```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = newArray[arr.length - i - 1];
  }
  return arr;
}
```
*A failure-inducing input for the buggy program, as a JUnit test is shown below.
```
@Test
public void testReversedFail() {
  int[] input1 = {3,4};
  assertArrayEquals(new int[]{4,3}, ArrayExamples.reversed(input1));
}
```
* An input that does not induce a failure, as a JUnit test is shown below. 
```
public void testReversedPass() {
  int[] input1 = { };
  assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
}
```
* The symptom, as the output of running the tests, is shown below. 

![JUnit terminal output](https://b2bomber2.github.io/cse15l-lab-reports/Photos/lab3-0.png)

* The bug, as the before-and-after code change required to fix it, is described below. 
```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = newArray[arr.length - i - 1];
  }
  return arr;
}
```
The code body of the loop needs to be changed. Since the elements of ```arr``` need to be transferred to ```newArray```, the correct code for the loop body is ```newArray[arr.length - i - 1] = arr[i];```. Afterward, ```newArray``` needs to be returned because a new array is the expected output. The revised code below passes both of the previous test cases. 
```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    newArray[arr.length - i - 1] = arr[i];
  }
  return newArray;
}
```

## Part 2: Researching Commands
<br />
For this section, I will choose to research the ```grep``` command. I used the command ```man grep``` and the following shows the resulting output. ```grep``` stands for global regular expression print and it returns text patterns as the output. 
```
GREP(1)                     General Commands Manual                    GREP(1)

NAME
     grep, egrep, fgrep, rgrep, bzgrep, bzegrep, bzfgrep, zgrep, zegrep,
     zfgrep – file pattern searcher

SYNOPSIS
     grep [-abcdDEFGHhIiJLlMmnOopqRSsUVvwXxZz] [-A num] [-B num] [-C num]
          [-e pattern] [-f file] [--binary-files=value] [--color[=when]]
          [--colour[=when]] [--context=num] [--label] [--line-buffered]
          [--null] [pattern] [file ...]

DESCRIPTION
     The grep utility searches any given input files, selecting lines that
     match one or more patterns.  By default, a pattern matches an input line
     if the regular expression (RE) in the pattern matches the input line
     without its trailing newline.  An empty expression matches every line.
     Each input line that matches at least one of the patterns is written to
     the standard output.

     grep is used for simple patterns and basic regular expressions (BREs);
     egrep can handle extended regular expressions (EREs).  See re_format(7)
     for more information on regular expressions.  fgrep is quicker than both
     grep and egrep, but can only handle fixed patterns (i.e., it does not
     interpret regular expressions).  Patterns may consist of one or more
     lines, allowing any of the pattern lines to match a portion of the input.

     zgrep, zegrep, and zfgrep act like grep, egrep, and fgrep, respectively,
     but accept input files compressed with the compress(1) or gzip(1)
     compression utilities.  bzgrep, bzegrep, and bzfgrep act like grep,
     egrep, and fgrep, respectively, but accept input files compressed with
     the bzip2(1) compression utility.

     The following options are available:

     -A num, --after-context=num
             Print num lines of trailing context after each match.  See also
             the -B and -C options.

     -a, --text
             Treat all files as ASCII text.  Normally grep will simply print
             “Binary file ... matches” if files contain binary characters.
             Use of this option forces grep to output lines matching the
             specified pattern.

     -B num, --before-context=num
             Print num lines of leading context before each match.  See also
             the -A and -C options.

     -b, --byte-offset
             The offset in bytes of a matched pattern is displayed in front of
             the respective matched line.

     -C num, --context=num
             Print num lines of leading and trailing context surrounding each
             match.  See also the -A and -B options.

     -c, --count
             Only a count of selected lines is written to standard output.

     --colour=[when], --color=[when]
             Mark up the matching text with the expression stored in the
             GREP_COLOR environment variable.  The possible values of when are
             “never”, “always” and “auto”.

     -D action, --devices=action
             Specify the demanded action for devices, FIFOs and sockets.  The
             default action is “read”, which means, that they are read as if
             they were normal files.  If the action is set to “skip”, devices
             are silently skipped.

     -d action, --directories=action
             Specify the demanded action for directories.  It is “read” by
             default, which means that the directories are read in the same
             manner as normal files.  Other possible values are “skip” to
             silently ignore the directories, and “recurse” to read them
             recursively, which has the same effect as the -R and -r option.

     -E, --extended-regexp
             Interpret pattern as an extended regular expression (i.e., force
             grep to behave as egrep).

     -e pattern, --regexp=pattern
             Specify a pattern used during the search of the input: an input
             line is selected if it matches any of the specified patterns.
             This option is most useful when multiple -e options are used to
             specify multiple patterns, or when a pattern begins with a dash
             (‘-’).

     --exclude pattern
             If specified, it excludes files matching the given filename
             pattern from the search.  Note that --exclude and --include
             patterns are processed in the order given.  If a name matches
             multiple patterns, the latest matching rule wins.  If no
             --include pattern is specified, all files are searched that are
             not excluded.  Patterns are matched to the full path specified,
             not only to the filename component.

      --exclude-dir pattern
             If -R is specified, it excludes directories matching the given
             filename pattern from the search.  Note that --exclude-dir and
             --include-dir patterns are processed in the order given.  If a
             name matches multiple patterns, the latest matching rule wins.
             If no --include-dir pattern is specified, all directories are
             searched that are not excluded.

     -F, --fixed-strings
             Interpret pattern as a set of fixed strings (i.e., force grep to
             behave as fgrep).

     -f file, --file=file
             Read one or more newline separated patterns from file.  Empty
             pattern lines match every input line.  Newlines are not
             considered part of a pattern.  If file is empty, nothing is
             matched.

     -G, --basic-regexp
             Interpret pattern as a basic regular expression (i.e., force grep
             to behave as traditional grep).

     -H      Always print filename headers with output lines.

     -h, --no-filename
             Never print filename headers (i.e., filenames) with output lines.

     --help  Print a brief help message.

     -I      Ignore binary files.  This option is equivalent to the
             “--binary-files=without-match” option.

     -i, --ignore-case
             Perform case insensitive matching.  By default, grep is case
             sensitive.

     --include pattern
             If specified, only files matching the given filename pattern are
             searched.  Note that --include and --exclude patterns are
             processed in the order given.  If a name matches multiple
             patterns, the latest matching rule wins.  Patterns are matched to
             the full path specified, not only to the filename component.

     --include-dir pattern
             If -R is specified, only directories matching the given filename
             pattern are searched.  Note that --include-dir and --exclude-dir
             patterns are processed in the order given.  If a name matches
             multiple patterns, the latest matching rule wins.

     -J, --bz2decompress
             Decompress the bzip2(1) compressed file before looking for the
             text.

     -L, --files-without-match
             Only the names of files not containing selected lines are written
             to standard output.  Pathnames are listed once per file searched.
             If the standard input is searched, the string “(standard input)”
             is written unless a --label is specified.

     -l, --files-with-matches
             Only the names of files containing selected lines are written to
             standard output.  grep will only search a file until a match has
             been found, making searches potentially less expensive.
             Pathnames are listed once per file searched.  If the standard
             input is searched, the string “(standard input)” is written
             unless a --label is specified.

     --label
             Label to use in place of “(standard input)” for a file name where
             a file name would normally be printed.  This option applies to
             -H, -L, and -l.

     --mmap  Use mmap(2) instead of read(2) to read input, which can result in
             better performance under some circumstances but can cause
             undefined behaviour.

     -M, --lzma
             Decompress the LZMA compressed file before looking for the text.

     -m num, --max-count=num
             Stop reading the file after num matches.

     -n, --line-number
             Each output line is preceded by its relative line number in the
             file, starting at line 1.  The line number counter is reset for
             each file processed.  This option is ignored if -c, -L, -l, or -q
             is specified.

     --null  Prints a zero-byte after the file name.

     -O      If -R is specified, follow symbolic links only if they were
             explicitly listed on the command line.  The default is not to
             follow symbolic links.

     -o, --only-matching
             Prints only the matching part of the lines.

     -p      If -R is specified, no symbolic links are followed.  This is the
             default.

     -q, --quiet, --silent
             Quiet mode: suppress normal output.  grep will only search a file
             until a match has been found, making searches potentially less
             expensive.

     -R, -r, --recursive
             Recursively search subdirectories listed.  (i.e., force grep to
             behave as rgrep).

     -S      If -R is specified, all symbolic links are followed.  The default
             is not to follow symbolic links.

     -s, --no-messages
             Silent mode.  Nonexistent and unreadable files are ignored (i.e.,
             their error messages are suppressed).

     -U, --binary
             Search binary files, but do not attempt to print them.

     -u      This option has no effect and is provided only for compatibility
             with GNU grep.

     -V, --version
             Display version information and exit.

     -v, --invert-match
             Selected lines are those not matching any of the specified
             patterns.

     -w, --word-regexp
             The expression is searched for as a word (as if surrounded by
             ‘[[:<:]]’ and ‘[[:>:]]’; see re_format(7)).  This option has no
             effect if -x is also specified.

     -x, --line-regexp
             Only input lines selected against an entire fixed string or
             regular expression are considered to be matching lines.

     -y      Equivalent to -i.  Obsoleted.

     -z, --null-data
             Treat input and output data as sequences of lines terminated by a
             zero-byte instead of a newline.

     -X, --xz
             Decompress the xz(1) compressed file before looking for the text.

     -Z, --decompress
             Force grep to behave as zgrep.

     --binary-files=value
             Controls searching and printing of binary files.  Options are:
             binary (default)  Search binary files but do not print them.
             without-match     Do not search binary files.
             text              Treat all files as text.

     --line-buffered
             Force output to be line buffered.  By default, output is line
             buffered when standard output is a terminal and block buffered
             otherwise.

     If no file arguments are specified, the standard input is used.
     Additionally, “-” may be used in place of a file name, anywhere that a
     file name is accepted, to read from standard input.  This includes both
     -f and file arguments.

macOS 14.2                     November 10, 2021                    macOS 14.2
```

<br />

From this list, I will be choosing ```-H```, ```-o```, ```-q```, and ```-v```. 

<br /> 

Here are 2 examples of the ```-H``` command-line option for the ```grep``` command. 
* ```
ferrariguan@HP-Laptop-15-MacOS biomed % grep -H summary ar328.txt  
ar328.txt:        In summary, males who have hypogonadism, regardless of
```
* ```
ferrariguan@HP-Laptop-15-MacOS biomed % grep -H mouse bcr45.txt
bcr45.txt:        BRCA1 expression patterns in mouse
bcr45.txt:        homozygous, BRCA1-deleted mouse models have resulted in
bcr45.txt:        5colony-forming units/ml on mouse cells (A9). Log phase
bcr45.txt:        one side of each mouse and NEO cells in matrigel on the
bcr45.txt:        occur in the mouse ovary (granulosa and thecal cells of
bcr45.txt:        mouse NIH3T3 cells [ 50]. In addition, increased
bcr45.txt:        BRCA1 transfected into mouse 3T3
```

<br />

The ```-H``` command-line option ensures that ```grep``` always prints the filename header with the output lines. So, as shown in the examples above, every line of the output starts with the file name and extension. 

<br />

Here are 2 examples of the ```-o``` command-line option for the ```grep``` command. 
* ```
ferrariguan@HP-Laptop-15-MacOS biomed % grep -o patients ar328.txt
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
patients
```
* ```
ferrariguan@HP-Laptop-15-MacOS biomed % grep -o retrovirus-mediated bcr45.txt
retrovirus-mediated
```

<br />

The ```-o``` command-line option ensures that ```grep``` prints only the lines that match the argument inside of the file. So, as shown in the examples above, every line of the output contains only the argument. 

<br />

Here are 2 examples of the ```-q``` command-line option for the ```grep``` command. 
* ```
ferrariguan@HP-Laptop-15-MacOS biomed % grep -q ratio ar328.txt
```
* ```
ferrariguan@HP-Laptop-15-MacOS biomed % grep -q machine bcr45.txt
```

<br /> 

The ```-q``` command-line option ensures that ```grep``` does not print its normal output. So, as shown in the examples above, nothing was printed due to the ```-q``` command-line option silencing the output. 

<br />

Here are 2 examples of the ```-v``` command-line option for the ```grep``` command. 
* ```
ferrariguan@HP-Laptop-15-MacOS biomed % grep -v the ar328.txt
      
        Introduction
        The clinical observation that sexual dimorphism plays a
        autoimmune diseases in females and an increased immune
        response to antigenic stimulus. These observations make it
        thymic-hypothalamic-pituitary-gonadic axis [ 1].
        Series of subjects with gonadal dysgenesis, and isolated
        cases of Klinefelter's syndrome associated with
        rheumatic/autoimmune diseases (RAD), suggest a relation
        patients reported to date who have hypogonadism and RAD are
        6, 7], lupus anticoagulant and antiphospholipid syndrome
        associated [ 8], scleroderma [ 9, 10, 11, 12], rheumatoid
        arthritis (RA) [ 13], ankylosing spondylitis (AS) [ 14, 15,
        16], and polymyositis [ 17], while Turner's syndrome has
        been associated with autoimmune thyroiditis [ 3], juvenile
        rheumatoid arthritis (JRA) [ 18], and juvenile-onset
        included eunuchoid males and female subjects with an
        abnormal X karyotype [ 2].
        male patients with untreated hypogonadism have an increased
      
      
        Methods
        The clinical criteria of male hypogonadism refers to
        failure of testicular function resulting in decreased
        production or absence of male sex hormones and impaired
        hypothalamic and pituitary dysfunction or is primary
        testicular failure [ 20].
        Mexico City, Mexico, from July 1998 to May 2000, 13 who
        were not receiving hormone substitution were selected for
        this study.
        The clinical criteria of male 'hypogonadism' refers to
        failure of testicular function resulting in decreased
        production or absence of male sex hormones and impaired
        hypothalamic and pituitary dysfunction or is primary
        testicular failure [ 20].
        Ten normogonadic healthy male hospital staff with
        control group for testicular size and hormone levels.
        and clinic evaluation, including a physical exam, in
        karyotyping of peripheral leukocytes. The presence of
        secondary sexual characteristics and testicular volume
        (normal value >20 ml) were noted.
        AS, psoriatic arthritis, JRA, polymyositis/dermatomyositis,
        scleroderma/CREST (calcinosis, Raynaud's phenomenon,
        esophageal dysfunction, sclerodactyly, telangiectasia), and
        Behcet's syndrome [ 22]. Venous blood (20 ml) was extracted
        (normal value <20 IU/ml), antinuclear antibodies by
        immunofluorescence test (rat kidney substrate), anti-DNA
        (radioimmunoassay), and Ro, La, Sm, and Scl-70 by
        nephelometry to disclose autoimmune phenomena and/or
        inflammatory serum subclinical abnormalities. The
        histocompatibility antigen B27 (B27) was determined by
        Terasaki's joint-to-thyroid function test (Cis bio
        international Groupe ORIS Cedex-France) using
        radioimmunoassay. Serum levels of testosterone
        (double-antibody radioimmunoassay technique), estradiol-17β
        (E 
        2 ) (International CIS Sorin, Paris,
        France; double-antibody radioimmunoassay kit),
        follicle-stimulating hormone, luteinizing hormone, and
        prolactin (Diagnostic Products Co, Los Angeles, CA, USA;
        double-antibody radioimmunoassay kit) (in duplicate) were
        determined in patients and controls. Coefficients of
        intra-assay and interassay variations were, respectively,
        as follows: testosterone, 6.0 and 10.4%; E 
        2 , 5.0 and 8.5%; follicle-stimulating
        hormone, 3.1 and 7.7%; luteinizing hormone, 7.0 and 7.9%;
        lumbosacral spine, sacroiliac joints, and affected
        peripheral joints and were interpreted blind. Affected
        signs.
        U test were used for statistical
        analysis (computer package Epi-Info, Version 6.00; Centers
        for Disease Control and Prevention, USA, World Health
        Organization, Geneva, Switzerland). The significance limit
        was set at 
        P < 0.05.
      
      
        Results
        Age and body mass index were similar in patients and
        controls (mean ± standard deviation): respectively, age
        25.3 ± 8.4 years vs 29.5 ± 7.6 years and body mass index
        23.1 ± 3.3 kg/m 2vs 24.2 ± 3.6 kg/m 2( 
        P =NS). The testicular volume was 4.4
        ± 4.3 ml in patients and 43.5 ± 3.5 ml in controls ( 
        had hypergonadotropic hypergonadism, five of whom had
        patients had hypogonadotropic hypogonadism (46,XY); two of
        this group had Kallmann's syndrome and two had idiopathic
        cryptorchidism.
        associated with anti-phospholipid antibodies), one had JRA,
        and one had juvenile dermatomyositis (Tables 1and 2). We
        did not find adult RA, scleroderma, scleroderma/CREST,
        psoriatic arthritis, or Behcet's syndrome.
        in those with and those without RAD. Serum testosterone and
        estradiol 17β levels were lower in those with RAD, but only
        ± 0.7 vs 2.7 ± 1.2 ng/ml, 
        P = 0.0005) (see Supplementary Table
        1).
      
      
        Discussion
        intentional search for RAD in male patients with untreated
        hypogonadism.
        Usually, males with hypogonadism diagnosed in infancy or
        in youth are those who have a complete hypogonadic clinical
        picture. Some individuals, however, exhibit an incomplete
        clinical picture and may reach adulthood without having
        light during tests of sterility in a couple, or during
        epidemiological studies [ 23, 24, 25, 26], which have
        hypogonadism.
        that causing Klinefelter's syndrome, whose prevalence is of
        25, 26] and 0.2 to 41.3% in populations with certain mental
        or behavioral problems [ 27, 28, 29].
        Our study was performed in a smaller group of male
        patients with hypogonadism to those that have been reported
        studied in an andrology clinic for infertility and thus are
        previously. Although it is arguable that our series of
        patients, not being a representative sample, is unsuitable
        hypogonadism, we investigated RAD only in those who had not
        possibility that androgen replacement had interfered with
        patients was severe, with clear systemic and articular
        had gone unnoticed until we looked for it.
        where our study was performed, is about 0.83% (including RA
        0.62%; SLE 0.03%; polymyositis/dermatomyositis 0.04%; JRA
        relatively large number of cases of RAD in this very small
        group of male patients with untreated hypogonadism was
        surprisingly high ( 
        P < 0.001), suggesting a strong
        Table 2). The development of RAD only in those patients
        with severe testicular dysfunction suggests that such
        dysfunction is one endogenous factor that predisposes to
        combination of B27 with AS. The frequency of patients with
        B27 (all of whom also developed AS) was very high (30.7%),
        hypogonadism will develop AS is higher than that of a
        healthy Mexican mestizo (about 4%, 
        P = 0.001) [ 33]. We cannot explain
        this association at present.
        The frequency of SLE in male patients with hypogonadism
        first case of hypogonadism associated with juvenile
        dermatomyositis. The development of dermatomyositis and JRA
        
        P = 0.006 and 
        P = 0.004, respectively;
        frequency of RA was no higher in our group of patients than
        hypogonadism are not related, as has already been suggested
        [ 13].
        heterogeneous (hypogonadism due to various causes, and
        increased frequency of RAD.
        Studies in healthy, normogonadic males with RAD have
        found low serum levels of testosterone and high levels of E
        
        2 in patients with RA, SLE, and
        Sjogren's syndrome [ 34, 35]. The inflamed tissues of
        normogonadic patients with RAD contain intense cellular
        infiltrates rich in macrophages. These cells have hormonal
        receptors capable of converting testosterone and
        androstenedione into estrone and E 
        2 by means of aromatase [ 36, 37, 38].
        in estrogens observed in patients with RA [ 38]. However,
        in our group of patients, serum testosterone and E 
        2 were both decreased. Therefore, in our
        testosterone decrease was not due to an increase in its
        conversion to E 
        without showing an increment from its conversion to E 
        studied, Bebo 
        et al. have shown that orchidectomy
        experimental autoimmune encephalomyelitis [ 39]. In humans,
        before treatment with androgens, patients who have
        Klinefelter's syndrome but not RAD have very diminished
        levels of testosterone associated with high levels of IgG,
        IgA, IgM, IL-2, and IL-4 and with an absolute increase of
        diminished level of testosterone is associated with low
        increases humoral and cellular immunity. When androgens are
        picture improves [ 30, 31].
        If our argument is correct, low serum testosterone
        2 . These differences could also explain
        ameliorated [ 30, 31, 38].
        In summary, males who have hypogonadism, regardless of
        testosterone.
      
      
        Abbreviations
        AS = ankylosing spondylitis; B27 = histocompatibility
        antigen B27; CREST = calcinosis, Raynaud's phenomenon,
        esophageal dysfunction, sclerodactyly, telangiectasia; E 
        2 = estradiol-17β JRA = juvenile
        rheumatoid arthritis; RA = rheumatoid arthritis; RAD =
        rheumatic/autoimmune disease; SLE = systemic lupus
```
* ```
ferrariguan@HP-Laptop-15-MacOS biomed % grep -v cell bcr45.txt
      
        Synopsis
        
          Introduction
          Germline mutations in the breast and ovarian cancer
          susceptibility gene 
          BRCA1 , which is located on
          chromosome 17q21, are associated with a predisposition to
          the development of cancer in these organs [ 1, 2]. No
          mutations in the 
          BRCA1 gene have been detected in
          sporadic breast cancer cases, but mutations have been
          detected in sporadic cases of ovarian cancer [ 3, 4].
          Although there is debate regarding the level of cancer
          risk associated with mutations in 
          BRCA1 and the significance of the
          lack of mutations in sporadic tumors, it is possible that
          alterations in the function of BRCA1 may occur by
          mechanisms other than mutation, leading to an
          underestimation of risk when it is calculated solely on
          the basis of mutational analysis. Such alterations cannot
          be identified until the function and regulation of BRCA1
          are better understood.
          The 
          BRCA1 gene encodes a 220-kDa
          nuclear phosphoprotein that is regulated in response to
          DNA damaging agents [ 5, 6, 7] and in response to
          estrogen-induced growth [ 8, 9, 10, 11]. Germline
          mutations that cause breast and ovarian cancer
          predisposition frequently result in truncated and
          presumably inactive BRCA1 protein [ 12].
          poorly differentiated ovarian adenocarcinoma [ 13]. This
          responsive and withdrawal of estrogen results in eventual
          stimulated as a result of estrogen treatment [ 8, 9, 10,
          death process [ 14]. Therefore, we examined the effect of
          response to hormone depletion as well as estrogen
          stimulation. The results suggest that reduced levels of
          BRCA1 correlates with a survival advantage when BG-1
          hormone-depleted conditions. In optimum growth
          conditions, significantly reduced levels of BRCA1
          correlates with enhanced growth both 
          in vitro and 
          in vivo .
        
        
          Aims
          To test the hypothesis that BRCA1 may play a role in
        
        
          Materials and methods
          which contains an abundant amount of estrogen receptors
          (600 fmoles/100 μg DNA), was infected using a pLXSN
          retroviral vector (provided by AD Miller) containing an
          inverted partial human cDNA 900-base-pair sequence of
          BRCA1 (from nucleotide 121 in exon 1 to nucleotide 1025
          in exon 11, accession #U14680). After 2 weeks of
          selection in 800 μg/ml of geneticin-G418 (Gibco/Life
          Technologies, Gaithersburg, MD, USA), BG-1 G418-resistant
          colonies were pooled, or individually isolated, and
          assayed for growth in the presence or absence of
          supplemented estrogen. Virally infected pooled
          levels by ribonuclease protection assay (Fig. 1a). BRCA1
          ribonuclease protection probe was made using an 
          in vitro transcription kit (Ambion,
          Inc, Austin, TX, USA) as previously described [ 10] and
          derived clones were tested for protein levels by Western
          blot analysis using an anti-BRCA1 (Oncogene Research,
          Ab-1, Cambridge, MA, USA) antibody. Growth curve analysis
          of Infected populations and were pretreated for 5 days in
          phenol red-free, Dulbecco's modified eagle medium
          (DMEM)/F-12 medium (Gibco/Life Technologies) supplemented
          with 10% charcoal/dextran treated serum (Hyclone, Logan,
          in triplicate in the absence or presence of estrogen (10
          -8mol/l; 17β-Estradiol; 1,3,5 (10) - Estratriene
          3,17β-diol; Sigma, St Louis, MO, USA). For soft agar
          assay, clones were plated into 10 60-mm dishes at 1 × 10
          without added estrogen (10 -8mol/l) in phenol red-free
          medium with 10% stripped serum in order to test for
          anchorage independent growth. BG-1 infected clones were
          Products, Bedford, MA, USA) into subcutaneous sites in
          6-week-old athymic Ncr-nude mice (NCI Animal Program,
          Bethesda, MD, USA) that were ovariectomized at
          approximately 4 weeks of age. Half of the ovariectomized
          mice received an implanted 0.18mg estrogen 60-day pellet
          (Innovative Research of America, Sarasota, FL, USA).
        
        
          Results
          Antisense technology was effective in decreasing both
          RNA and protein levels of BRCA1 in the BG-1 human ovarian
          populations contained significantly less BRCA1 message
          than control LXSN-infected pools and selected clones
          contained varying reduced levels of BRCA1 protein
          compared with control clones (Figs 1aand 1b).
          Three independent BRCA1 antisense-infected cultures
          withdrawal from estrogen over a 6- to 20-day period (Fig.
          2a). The BRCA1 antisense population also exhibited a
          BG-1 BRCA1 antisense clones demonstrated a similar
          response to pooled population studies, enhanced growth
          with estrogen, and failure to die upon estrogen depletion
          (Fig. 2b).
          The BRCA1 antisense clones were further examined for
          other associated tumorigenic properties. All of the
          antisense clones were able to form colonies in soft agar
          whereas control clones were deficient in their ability to
          Table 1shows, in the presence of estrogen, the clone with
          the lowest levels of BRCA1 (AS-4) produced significantly
          than the control clone (NEO; 6 ± 3.1 colonies per 10
          with matrigel subcutaneously into ovariectomized athymic
          mice. Almost twice as many sites were positive for the
          AS-4 clone (14 out of 14) as for the NEO clone (eight out
          of 14) 42 days after injection. In addition, BRCA1
          antisense tumors averaged twice the size of control
          implanted estrogen (11 days versus 21 days until tumor
          formation).
        
        
          Discussion
          The present studies show that reduction in BRCA1
          levels, using an antisense retroviral vector in the
          contributes to confirmation of the hypothesis that 
          BRCA1 plays a pivotal role in the
          BRCA1 RNA and protein levels were
          successfully reduced in populations and isolated clones
          conditions in monolayer or soft agar conditions.
          Furthermore, a BRCA1 antisense clone that had
          significantly low levels of BRCA1 protein was able to
          form twice as many tumors in ovariectomized nude mice
          with a decreased latency compared with a control
          clone.
          important for the maintenance of normal healthy tissues.
          In support of this hypothesis, it has been shown that 
          p53 and 
          BRCA1 can form stable complexes,
          and can coactivate 
          p21 and 
          bax genes, which may lead to the
          activation of the apoptosis pathway [ 15]. The present
          have a survival advantage in conditions where control
          BRCA1 levels appear to affect the
          of estrogenic growth-inducing conditions. Although
          mutations in this gene are uncommon in sporadic breast
          and ovarian tumors, 
          BRCA1 expression levels and protein
          levels have been found to be reduced in sporadic human
          breast carcinomas [ 16, 17, 18, 19]. In addition it has
          been demonstrated [ 20] that hormone-dependent tumors
          such as breast and ovarian cancers have a decreased
          ability to undergo apoptosis. Other mechanisms involving
          gene regulation may allow for decreased expression of 
          BRCA1 in sporadic tumors. The
          response of 
          BRCA1 mRNA and protein levels to
          mitogens and hormones 
          in vitro suggests that 
          BRCA1 may play a role in regulation
          product may be involved in the regulation of hormone
          response pathways, and the present results demonstrate
          that loss of BRCA1 may result in loss of inhibitory
          control of these mitogenic pathways. These studies show
          that reduction in 
          BRCA1 mRNA and protein can result
          in both 
          in vitro and 
          in vivo conditions, suggesting that
          
          BRCA1 may normally be acting as a
          growth inhibitor. Low BRCA1 levels found in sporadic
          cancers may be an important factor in tumorigenesis. The
          present data suggest that diminished levels of 
          BRCA1 not only accelerate
          but also appear to promote tumorigenesis. We propose that
          the loss or reduction of 
          population to neoplastic transformation by altering the
          rendering it more sensitive to secondary genetic
          changes.
        
      
      
        Introduction
        Germline mutations in the breast and ovarian cancer
        susceptibility gene 
        BRCA1 , which is located on
        chromosome 17q21, are associated with a predisposition to
        the development of cancer in these organs [ 1, 2]. Initial
        analyses [ 22] suggested that women with germline mutations
        in the 
        BRCA1 gene and a strong family
        history of breast or ovarian cancer have 85 and 44%
        lifetime risks of developing breast and ovarian cancer,
        respectively. Recent studies [ 23], however, have suggested
        that analyses based on women who were not selected for a
        familial history of cancer indicate that the risk for
        cancer associated with mutations in these genes is 50 and
        16% for breast and ovarian cancers, respectively. No
        mutations in the 
        BRCA1 gene have been detected in
        sporadic breast cancer cases; however, mutations have been
        detected in sporadic cases of ovarian cancer [ 3, 4].
        Although there is debate regarding the level of cancer risk
        associated with mutations in 
        BRCA1 and the significance of the
        lack of mutations in sporadic tumors, it is possible that
        alterations in the function of BRCA1 may occur by
        mechanisms other than mutation. This would lead to an
        underestimation of risk when it is calculated solely on the
        basis of mutational analysis. Such alterations cannot be
        identified until the function and regulation of BRCA1 are
        better understood.
        The 
        BRCA1 gene encodes a 220-kDa nuclear
        protein that may be regulated by phosphorylation through
        6, 7]. The level of BRCA1 is also regulated in response to
        estrogen or estrogen-induced growth in breast [ 8, 9, 10,
        including BARD-1 [ 24], Rad51, PCNA, and BRCA2 [ 7, 25]. In
        addition, BRCA1 can act as a transcriptional transactivator
        in yeast reporter assays [ 26, 27] and binds the RNA
        polymerase II holoenzyme, a component of the basal
        transcription machinery [ 25]. The precise mechanism of
        action and the specific signaling pathway affected by BRCA1
        remain unknown, however.
        Studies of 
        BRCA1 expression patterns in mouse
        tissue reveal that BRCA1 is most highly expressed in
        tissues undergoing rapid proliferation and differentiation,
        and that expression 
        in vivo is also hormone responsive.
        For example, analyses of mammary gland growth and
        development show high levels of BRCA1 expression in
        terminal end buds during puberty and in budding alveoli
        during pregnancy. In addition, hormonal stimulation in
        ovariectomized mice results in induction of BRCA1
        expression in the breast [ 28]. Attempts to develop
        homozygous, BRCA1-deleted mouse models have resulted in
        embryonic lethality [ 29, 30]. For example, when the 
        BRCA1 gene deletion was targeted in
        exons 5 and 6, mutant mice died before day 7.5 of
        embryogenesis. Analysis of DNA synthesis in the mutant
        suggesting that BRCA1 may paradoxically play a positive
        Most of the mechanistic BRCA1 studies to date have been
        decided to conduct a study to determine the effect of BRCA1
        patient with stage III, poorly differentiated ovarian
        wild-type BRCA1, is estrogen responsive, and withdrawal of
        suggested that BRCA1 is stimulated as a result of estrogen
        treatment [ 8, 9, 10, 11], and that BRCA1 may be involved
        are subjected to growth restrictive and hormone-depleted
        of BRCA1 protein have a distinct advantage for survival. In
        addition, significant reduction in BRCA1 protein level
        correlates with enhanced estrogen proliferation when
        BRCA1 levels, grown under optimal growth conditions both 
        in vitro and 
        in vivo .
      
      
        Materials and methods
        
          The estrogen receptor-positive, BG-1 line [ 13], which
          contains an abundant amount of estrogen receptors (600
          fmol/100 μg DNA), was provided by J Boyd (Sloan-Kettering
          Cancer Center, New York, NY, USA). GPE86 and PA317 viral
          were maintained in Dulbecco's modified eagle medium
          (DMEM)/F12 medium supplemented with 10% fetal calf serum
          (Summit, Fort Collins, CO, USA), and 50 units/ml
          radiation consistent with a wildtype 
          tested negative for mycoplasmas.
        
        
          Retroviral vector preparation and infection of
          A partial human cDNA sequence of 
          BRCA1 (from nucleotide 121 in exon
          1 to nucleotide 1025 in exon 11, accession #U14680) was
          inserted in the antisense orientation into the EcoR1 site
          of the pLXSN retroviral vector (provided by AD Miller).
          The vector alone, or the antisense 
          BRCA1 vector, was transfected using
          the calcium-phosphate precipitation method into the
          [ 31] in the presence of 4 μg/ml polybrene (Abbott
          were grown in selection media for 2 weeks and pooled for
          supernatant collection. Supernatants were filtered (0.20
          efficiencies of the LXSN virus ranged from 10 4to 10
          the LXSN control retrovirus or retroviruses containing
          the antisense 
          BRCA1 cDNA sequence. After 2 weeks
          of selection in 800 μg/ml of geneticin-G418 (Gibco/Life
          Technologies, Gaithersburg, MD, USA), BG-1 G418-resistant
          colonies were pooled or individually isolated and assayed
          for growth in the presence or absence of supplemented
          estrogen. Only isolated clones were used in anchorage
          dependence and tumorigenicity studies.
        
        
          BRCA1 ribonuclease protection assay and protein
          analysis
          A BRCA1 ribonuclease protection probe was made using
          an 
          In Vitro Transcription Kit (Ambion,
          Inc, Austin, TX, USA). The DNA template spanned part of
          exon 22, all of exon 23, and part of exon 24 of the 
          BRCA1 gene. Template DNA was
          incubated for 45min at 37°C with (α- 32P)-uridine
          triphosphate and T7 polymerase in the presence of buffer
          and nucleotides. DNA template was removed by
          ribonuclease-free deoxyribonuclease incubation at 37°C
          for 30min. The reaction was stopped by the addition of
          0.5 mol/l ethylenediaminetetra-acetic acid, and the
          labeled probe was purified on a 5% polyacrylamide gel.
          Sample RNA (20μg total RNA) was coprecipitated with the
          BRCA1 probe and the cyclophilin control probe [ 32],
          resuspended in Hyb-speed RPA (Ambion) hybridization
          buffer at 95°C, and then incubated at 68°C for 10min.
          Ribonuclease was added and the sample was incubated for
          45min at 37°C. Protected fragments were precipitated, and
          resuspended in loading buffer, followed by separation on
          a 5% polyacrylamide-urea gel, and exposed to X-ray
          film.
          BRCA1 protein was analyzed by Western blot analysis.
          dodecyl sulfate-polyacrylamide gel electrophoresis gel,
          anti-BRCA1 (Ab-1; Oncogene Research, Cambridge, MA, USA)
          antibody as previously described [ 10].
        
        
          Estrogen treatment and growth curve analysis
          G418-resistant colonies from 
          pretreated for 5 days in phenol red-free, DMEM/F-12
          medium (Gibco/Life Technologies) supplemented with 10%
          charcoal/dextran treated serum (Hyclone, Logan, UT, USA),
          triplicate for growth curve analysis in the absence or
          presence of estrogen (10 -8mol/l; 17β-Estradiol; 1,3,5
          (10) - Estratriene 3, 17β-diol; Sigma, St Louis, MO,
          USA). Extended growth curve analysis was plated at 2.5 ×
          10 6in 100mm dishes for an extended treatment of 20 days
          without estrogen. Clones were isolated from the 
          BRCA1 antisense and LXSN BG-1
          pooled populations and grown in phenol red-free,
          DMEM/F-12 medium (Gibco/Life Technologies) supplemented
          with charcoal/dextran treated serum (Hyclone) for 5 days
          before plating for growth curve analysis. Cells were then
          either the absence or presence of estrogen (10 -8mol/l)
          and grown for 8-10 days. Cell number was calculated on
          indicated days using a Coulter counter. The number of
          using a hemocytometer. Statistical analyses of 
          P values were calculated based on
          the fold differences between growth of the clones by
          computing a mean ratio and the corresponding standard
          deviation [ 33].
        
        
          Anchorage independence analysis and
          tumorigenicity
          Selected BG-1 clones were tested for anchorage
          independent growth in 0.3% bacto-peptone agar with a 0.6%
          bacto-peptone agar base plus or minus added estrogen (10
          -8mol/l) in phenol red-free medium with 10% stripped
          serum. Each BG-1, neomycin-resistant clone was plated
          after 14 days. Pairwise comparisons were made by a
          two-sided Mann-Whitney U test to calculate 
          P values [ 34].
          BG-1-infected clones were tested for tumorigenicity in
          6-week-old athymic Ncr-nude mice (NCI Animal Program,
          Bethesda, MD, USA) that were ovariectomized at
          approximately 4 weeks of age. BRCA1 antisense clone
          Collaborative Biomedical Products, Bedford, MA, USA) into
          two subcutaneous sites on one side of 16 mice (32
          injection sites), whereas a LXSN control clone was
          injected on the opposite side of the same mice. Nine of
          the 16 ovariectomized mice also received an implanted
          0.18mg estrogen 60-day pellet (Innovative Research of
          America, Sarasota, FL, USA). Mice were periodically
          examined and tumor size was measured during the 3-month
          period after injection.
        
      
      
        Results
        
          Effective decrease in BRCA1expression using
          antisense technology
          Antisense technology was effective in decreasing both
          RNA and protein levels of BRCA1 in the BG-1 human ovarian
          of an antisense 900 base-pair cDNA sequence of the
          amino-terminal region of 
          BRCA1 . Three experiments (two of
          which were from independently made supernatants) showed
          that infection of pLXSN (vector alone) and 
          BRCA1 antisense retroviral
          colonies at similar rates (titers ranged from 0.78 to 4.2
          × 10 4colony-forming units/ml). The same vectors were
          efficiency of 6.3×10 -5for the anti-sense 
          BRCA1 or 9.9 × 10 -5for the control
          plasmid (pLXSN). Neomycin-resistant colonies were pooled
          and examined for 
          BRCA1 message levels by
          ribonuclease protection assay. 
          contained significantly less 
          BRCA1 message than control LXSN
          absence of estrogen (Fig. 1a). Although there appears to
          be no detectable amounts of BRCA1 RNA present after
          estrogen withdrawal, low levels of protein can be
          detected by western blot analysis [ 10].
          Subclones were also isolated from BRCA1 antisense
          blot analysis demonstrated that all of the antisense
          BRCA1 clones had reduced levels of BRCA1 protein compared
          with the NEO clones, and one antisense clone (AS-4) had
          very low levels of BRCA1 protein, although it was not
          totally absent (Fig. 1b).
        
        
          Effects of reduced BRCA1expression on in
          vitrogrowth
          Pooled populations of antisense 
          BRCA1 BG-1 colonies were examined
          for growth in the absence or presence of supplemented
          estrogen. Three independently infected cultures of 
          estrogen over a 6-day period, as well as a threefold to
          order to investigate further whether reduction of BRCA1
          estrogen-deprived conditions for an extended period of
          time. During the first 5 days, both groups continued to
          proliferate in the absence of estrogen, but the BRCA1
          antisense group continued to grow for the next 10 days,
          In order to avoid the problem of a mixed population of
          isolated from infected populations of 
          2bshows BG-1 parental and NEO clones exhibited up to a
          estrogen withdrawal, whereas antisense 
          BRCA1 clones showed as much as a
          period. In an attempt to determine if increased survival
          number of trypan blue positive, non-viable were examined
          after 14 days without estrogen. There were 5-10-fold more
          parental and NEO clone) then in the 
          BRCA1 antisense clone AS-4 (data
          plays a significant role in the survival of 
          withdrawal. Figure 2bagain demonstrates the ability of
          the BRCA1 antisense sub-clones to survive estrogen
          deprivation. In the presence of estrogen, three out of
          the four antisense 
          BRCA1 clones exhibited a growth
          advantage over NEO clones or the BG-1 parental population
          (Fig. 2b). Antisense 
          BRCA1 clones 1, 3 and 4 showed a
          and 8 after estrogen treatment compared with only a
          which had the lowest levels of BRCA1 protein, showed a
          highly significant (16-fold; 
          P <0.01) stimulation of growth
          between days 5 and 8 of estrogen induction (Figs 2band
          4). In summary, although three out of four of the
          antisense 
          BRCA1 clones had a growth advantage
          in the presence of estrogen, all four antisense 
          BRCA1 clones showed enhanced
          survival in estrogen-depleted media.
        
        
          Anchorage independent growth of BG-1 clones
          Anchorage independent growth is a common property of
          BRCA1 antisense subclones were also
          studied for anchorage independent growth in a semisoft
          agar medium with and without supplemented estrogen.
          Table1 shows that colony formation efficiencies on
          plastic of control (NEO) and 
          similar in estrogen-depleted and estrogen-containing
          media. However, the BG-1 control clone (NEO) was unable
          plated) in agar without the addition of estrogen, whereas
          the BG-1 antisense 
          BRCA1 clone was able to form soft
          agar colonies in estrogen depleted conditions (10 ± 2.9
          estrogen, both NEO and AS-4 were able to form colonies;
          however, there was a significant difference ( 
          P <0.01) in the ability to form
          colonies in agar between AS-4 (133 colonies) and the
          control clone (six colonies). These data suggest a
          correlation between the loss of BRCA1 protein and an
          increased survival/growth advantage in
          anchorage-independent conditions.
        
        
          Effects of reduced BRCA1 protein on in vivo tumor
          Because the AS-4 clone showed a growth advantage in
          soft agar, a phenotype that may be correlated with the
          ability to form tumors 
          in vivo , the BRCA1 antisense
          sub-clone AS-4 was evaluated for its ability to form
          subcutaneous tumors in ovariectomized athymic mice in the
          presence or absence of an estrogen pellet. Mice were
          other side. Of the mice injected, 50% received an
          implanted estrogen pellet (0.18 mg estrogen) that was
          designed to release estrogen for 60 days. In the absence
          of estrogen, a significant difference was detected in
          Almost twice as many sites were tumor positive for the
          AS-4 clones than for NEO injected sites. 100% (14/14)
          Tumor formation was reached for all AS-4 clones 42 days
          after injection, compared with 57% (eight out of 14)
          positive tumor formation of the NEO sites (Fig. 5b, upper
          the size of NEO control tumors (Fig. 5b, lower
          panel).
          athymic male or female mice (0 positive sites/20 sites
          large, progressively growing tumors when injected with
          matrigel in the presence of estrogen (Fig. 5a). These
          tumors were very large (>1cm diameter) and did not
          regress even though the estrogen pellet was effective for
          only 60 days (Fig. 5a, lower panel). Similar to the agar
          experiments, both the BRCA1 antisense clone and LXSN
          control clone were positive for tumor formation in the
          implanted estrogen (Fig. 5a, upper panel; 11 days versus
          21 days until tumor formation). Neither AS-4 nor NEO
          of estrogen, however. All tumors in the mice without
          estrogen pellets had started to regress by 71 days after
          injection. The observed tumor regression was not
          surprising, because matrigel is not stable for longer
          than 14 days in culture, and probably not 
          in vivo either (personal
          communication; Collaborative Biomedical Products,
          Bedford, MA, USA). By day 71, the matrigel would no
          longer confer an optimal growth environment for BG-1
        
        
          Discussion
          The present studies show that reduction of BRCA1
          levels, using an antisense retroviral vector in the
          aid in confirmation of the hypothesis that 
          BRCA1 functions as a tumor
          suppressor gene by playing a pivotal role in the balance
          BRCA1 RNA and protein levels were
          successfully reduced in pooled and isolated subclones of
          BRCA1 levels appeared to affect the
          absence of estrogenic growth-inducing conditions. We
          found that 
          pooled populations and individual subclones, also
          exhibited enhanced growth in monolayer culture on plastic
          in the presence of estrogen compared with control
          vector-infected colonies. All BRCA1 antisense subclones
          were able to proliferate as well as exhibit a decreased
          death rate in estrogen-deprived media, whereas parental
          and control subclones failed to grow. Death after
          estrogen withdrawal has been shown in previous studies
          demonstrated other traits associated with a tumorigenic
          phenotype, such as the ability to grow in soft agar
          independent of estrogen, whereas control clones could
          only form colonies with the addition of estrogen. In
          ovariectomized nude mice, a BRCA1 antisense clone (AS-4)
          was examined for tumorigenicity compared with a control
          clone (NEO). The AS-4 clone formed a greater number of
          and larger tumors than NEO in the absence of estrogen,
          and in general formed tumors faster in the presence of
          estrogen. The main conclusion from these studies is that
          BG-1 clones with reduced levels of BRCA1 protein have a
          survival advantage over controls in the absence of
          estrogen both 
          in vitro and 
          in vivo. 
          The response of 
          BRCA1 mRNA and protein levels to
          mitogens and hormones 
          in vitro suggests that 
          BRCA1 may play a role in regulation
          hormones and growth factors interact in a complex manner
          which are then balanced with growth inhibitors [ 36, 37,
          38, 39, 40]. The mechanism by which 
          BRCA1 can regulate or influence
          these processes has not yet been identified. It has been
          shown that 
          BRCA1 is induced as a result of the
          mitogenic activity of the estrogen receptor in estrogen
          stimulation is not required for 
          BRCA1 transcription, however [ 9,
          41]. In support of this, 
          BRCA1 expression has been shown to
          small and medium follicles) independent of hormonal
          status, and even in ovaries from estrogen receptor -/-
          deficient mice [ 41, 42]. In contrast, the tumors from
          patients with 
          BRCA1 mutations appear to have
          downregulation of estrogen receptors [ 43, 44, 45].
          Previous experiments in our laboratory showed that
          another hormone, progesterone, could also cause a modest
          increase of 
          exposure without an increase in growth (unpublished
          proliferation and induce apoptosis significantly in two
          BRCA1 may not be regulated directly
          by hormones, the BRCA1 gene product may be involved in
          the regulation of hormone response pathways, and the
          present results may demonstrate that loss of BRCA1 may
          result in loss of inhibitory control of these mitogenic
          pathways.
          
          BRCA1 transcription is regulated
          the G1/S-phase boundary [ 5, 9, 41, 47, 48, 49]. The
          present studies show that reduction of 
          BRCA1 mRNA and protein can result
          in vitro and 
          in vivo , suggesting that 
          BRCA1 may normally be acting as a
          growth inhibitor. Similar to our findings with ovarian
          independence and tumorigenicity is associated with 
          BRCA1 antisense introduction into
          oligonucleotides to 
          BRCA1 [ 51]. Conversely,
          introduction of full-length 
          BRCA1 by retrovirus-mediated gene
          transfer inhibited growth of breast and ovarian cancer
          in vitro and 
          in vivo experiments [ 51], and
          transfection of 
          inhibited new DNA synthesis by 50% in addition to
          inhibition of S-phase progression, possibly through
          p21 WAF1/CIP1[ 49].
          important for the maintenance of normal healthy tissues.
          This is especially important during early embryonic
          development as well as in the development and function of
          testes) [ 41, 48]. For example, 
          BRCA1 expression is critical during
          development, as evidenced by the embryonic lethality in
          transgenic knockout mice [ 29, 30, 52]. Alternatively,
          overexpression of 
          BRCA1 may activate apoptosis or
          wild-type 
          BRCA1 cDNA demonstrated a threefold
          to sixfold increase in chemosensitivity, as well as an
          increased susceptibility to drug-induced apoptosis [ 53].
          We found that clones with even moderately reduced levels
          of 
          BRCA1 protein appeared to be
          relatively resistant to death due to estrogen
          deprivation. Previous studies in our laboratory showed
          to gamma radiation were consistent with a 
          p53 wildtype phenotype, indicating
          that loss of estrogen dependence is probably not due to a
          
          p53 mutation (unpublished data).
          Shao 
          et al [ 14] demonstrated that 
          BRCA1 transfected into mouse 3T3
          In support of this hypothesis, it has been shown that 
          p53 and 
          BRCA1 can form stable complexes,
          and can coactivate 
          p21 and 
          bax genes, which may lead to the
          activation of the apoptosis pathway [ 15]. The present
          have a survival advantage in conditions where control
          Like 
          p53 , 
          BRCA1 has also been implicated in
          DNA damage and repair pathways [ 7, 48, 54]. According to
          BRCA1 activity may accumulate
          genetic alterations as a result of failure to arrest and
          repair DNA damage or self-destruct, thereby leading to
          genomic instability and neoplastic progression. It may
          not be coincidental that 
          BRCA1 -mutant breast cancers are
          preferentially linked to a 'specific' histopathologic
          aneuploidy, and hormone receptor-negative status [ 45].
          In addition, it has been demonstrated [ 20] that
          hormone-dependent tumors such as breast and ovarian
          cancers have a decreased ability to undergo apoptosis.
          Although mutations in this gene are uncommon in sporadic
          breast and ovarian tumors, 
          BRCA1 expression levels and protein
          levels have been found to be reduced in sporadic human
          breast carcinomas [ 16, 17, 18, 19]. Other mechanisms
          that involve gene regulation may allow for decreased
          expression of 
          BRCA1 in sporadic tumors.
          Hypermethylation has been observed in some sporadic
          breast tumors in the promoter region of 
          BRCA1 , which may account for
          decreased 
          BRCA1 transcription [ 55]. Low
          BRCA1 levels found in sporadic cancers may play an
          important role in tumorigenesis. The present data suggest
          that diminished levels of BRCA1 not only accelerate
          but appear to alter tumorigenesis. The exact mechanism
          may be unknown, but decreased 
          BRCA1 levels appear to affect the
          ability to arrest growth or die in the absence of
          estrogenic growth-inducing conditions. We propose that
          the loss or reduction of 
          population to neoplastic transformation by altering the
          rendering it more sensitive to secondary genetic
          changes. 
```

<br />

The ```-v``` command-line option ensures that ```grep``` does not print anything that matches the argument. So, as shown in the examples above, everything that did not match the argument was printed as the output. 
