---
title: 10 Known Open Source Projects in Iris Recognition 2018
author: Denis Trofimov
type: post
date: 2018-06-06T20:33:50+00:00
url: /10-known-open-source-projects-in-iris-recognition-2018/
featured_image: Eye-Photo-by-Tom-Tolkien.jpg
accesspress_mag_post_template_layout:
  - global-template
accesspress_mag_sidebar_layout:
  - global-sidebar
categories:
  - iris recognition
tags:
  - c++
  - code
  - dataset
  - iris recognition
  - iris segmentation
  - matlab
  - open source
  - project
  - python

---
<span style="font-weight: 400;">I found this pretty good list of </span>[<span style="font-weight: 400;">Iris Recognition open-source codes</span>][1]<span style="font-weight: 400;">. I am really appreciate work of the first author, </span>[<span style="font-weight: 400;">thanhkien84</span>][2]<span style="font-weight: 400;">. I asked myself, how to improve it? I have decided to add my value.</span>

<span style="font-weight: 400;">I have checked all links and found replacements for stale links to projects </span><span style="font-weight: 400;">OSIRIS, UND.</span>

<span style="font-weight: 400;">In the year 2003 there was only one iris recognition open source code from Libor Masek. His source code, written in Matlab, has been the baseline for generations of iris recognition coders. Recently there are a number of new open source codes come up. They are more mature and meet state-of-the-art accuracy. I summarise them in a list here for your reference.</span><!--more-->

<table>
  <tr>
    <td rowspan="2">
      <h2>
        <b>I</b><span style="font-weight: 400;">ris recognition projects</span>
      </h2>
    </td>
    
    <td rowspan="2">
      <b>Year/ Language</b>
    </td>
    
    <td rowspan="2">
      <b>Approach</b>
    </td>
    
    <td colspan="3">
      <b>Performance (EER)</b>
    </td>
  </tr>
  
  <tr>
    <td>
      <b>ICE 2005</b>
    </td>
    
    <td>
      <b>MBGC portal</b>
    </td>
    
    <td>
      <b>CASIA</b>
    </td>
  </tr>
  
  <tr>
    <td>
      <span style="font-weight: 400;">Libor Masek [</span><a href="http://www.peterkovesi.com/studentprojects/libor/"><span style="font-weight: 400;">project</span></a><span style="font-weight: 400;">]</span>
    </td>
    
    <td>
      <span style="font-weight: 400;">2003,</span></p> 
      
      <p>
        <span style="font-weight: 400;">Matlab</span></td> 
        
        <td>
          <span style="font-weight: 400;">Hough Circle + 1D Log-Gabor</span>
        </td>
        
        <td>
        </td>
        
        <td>
        </td>
        
        <td>
        </td></tr> 
        
        <tr>
          <td>
            <span style="font-weight: 400;">OSIRIS 4.1 [</span><a href="http://svnext.it-sudparis.eu/svnview2-eph/ref_syst/Iris_Osiris_v4.1/"><span style="font-weight: 400;">project dead link</span></a><span style="font-weight: 400;">]</span>
          </td>
          
          <td>
            <span style="font-weight: 400;">2013,</span></p> 
            
            <p>
              <span style="font-weight: 400;">C++</span></td> 
              
              <td>
                <span style="font-weight: 400;">Least square, Circle + 2D Gabor</span>
              </td>
              
              <td>
                <span style="font-weight: 400;">1.09%</span>
              </td>
              
              <td>
              </td>
              
              <td>
              </td></tr> 
              
              <tr>
                <td>
                  <span style="font-weight: 400;">5455945</span><span style="font-weight: 400;">/</span><a href="https://github.com/5455945/Iris_Osiris"><span style="font-weight: 400;">Iris_Osiris</span></a></p> 
                  
                  <p>
                    <span style="font-weight: 400;">(OSIRIS 4.1 fork) </span><span style="font-weight: 400;">Support OpenCV3.0+,OpenCV2.4.13</span></td> 
                    
                    <td>
                      <span style="font-weight: 400;">2017, C++</span>
                    </td>
                    
                    <td>
                      <span style="font-weight: 400;">Same as OSIRIS 4.1</span>
                    </td>
                    
                    <td>
                    </td>
                    
                    <td>
                    </td>
                    
                    <td>
                    </td></tr> 
                    
                    <tr>
                      <td>
                        <a href="https://github.com/vonclites/syris"><span style="font-weight: 400;">Python interface to OSIRIS Iris Segmentation and Recognition software </span></a><span style="font-weight: 400;">(OSIRIS 4.1 fork)</span>
                      </td>
                      
                      <td>
                        <span style="font-weight: 400;">2017, Python</span>
                      </td>
                      
                      <td>
                        <span style="font-weight: 400;">Same as OSIRIS 4.1</span>
                      </td>
                      
                      <td>
                      </td>
                      
                      <td>
                      </td>
                      
                      <td>
                      </td>
                    </tr>
                    
                    <tr>
                      <td>
                        <span style="font-weight: 400;">VASIR 2.2 [</span><a href="http://www.nist.gov/itl/iad/ig/vasir.cfm"><span style="font-weight: 400;">project</span></a><span style="font-weight: 400;">]</span>
                      </td>
                      
                      <td>
                        <span style="font-weight: 400;">2013,</span></p> 
                        
                        <p>
                          <span style="font-weight: 400;">C++</span></td> 
                          
                          <td>
                            <span style="font-weight: 400;">Circle + 2D Gabor</span>
                          </td>
                          
                          <td>
                            <span style="font-weight: 400;">3.5%</span>
                          </td>
                          
                          <td>
                            <span style="font-weight: 400;">13.9% best quality frame</span></p> 
                            
                            <p>
                              <span style="font-weight: 400;">30.6% all frames</span></td> 
                              
                              <td>
                              </td></tr> 
                              
                              <tr>
                                <td>
                                  <span style="font-weight: 400;">NonidealIRIS [project]</span>
                                </td>
                                
                                <td>
                                  <span style="font-weight: 400;">2006,</span></p> 
                                  
                                  <p>
                                    <span style="font-weight: 400;">Matlab</span></td> 
                                    
                                    <td>
                                      <span style="font-weight: 400;">Ellipse +  2D, Gabor</span>
                                    </td>
                                    
                                    <td>
                                    </td>
                                    
                                    <td>
                                    </td>
                                    
                                    <td>
                                    </td></tr> 
                                    
                                    <tr>
                                      <td>
                                        <span style="font-weight: 400;">USIT</span></p> 
                                        
                                        <p>
                                          <span style="font-weight: 400;">[</span><a href="http://www.wavelab.at/sources/USIT/"><span style="font-weight: 400;">project</span></a><span style="font-weight: 400;">]</span></td> 
                                          
                                          <td>
                                            <span style="font-weight: 400;">2016,</span></p> 
                                            
                                            <p>
                                              <span style="font-weight: 400;">C++</span></td> 
                                              
                                              <td>
                                                <span style="font-weight: 400;">Circle/Ellipse+</span></p> 
                                                
                                                <p>
                                                  <span style="font-weight: 400;">1D Log Gabor/</span>
                                                </p>
                                                
                                                <p>
                                                  <span style="font-weight: 400;">2D Gabor/</span>
                                                </p>
                                                
                                                <p>
                                                  <span style="font-weight: 400;">DCT/ SIFT/</span>
                                                </p>
                                                
                                                <p>
                                                  <span style="font-weight: 400;">SURF/LBP</span></td> 
                                                  
                                                  <td>
                                                  </td>
                                                  
                                                  <td>
                                                  </td>
                                                  
                                                  <td>
                                                    <span style="font-weight: 400;">0.82%</span>
                                                  </td></tr> 
                                                  
                                                  <tr>
                                                    <td>
                                                      <span style="font-weight: 400;">UND</span></p> 
                                                      
                                                      <p>
                                                        <span style="font-weight: 400;">[</span><a href="https://ideacenter.nd.edu/commercialization-engine/for-industry/available-technologies/software-available-for-license/iris-recognition-based-on-human-intrepretable-features/"><span style="font-weight: 400;">project</span></a><span style="font-weight: 400;">]</span></td> 
                                                        
                                                        <td>
                                                          <span style="font-weight: 400;">2016,</span></p> 
                                                          
                                                          <p>
                                                            <span style="font-weight: 400;">Matlab</span></td> 
                                                            
                                                            <td>
                                                              <span style="font-weight: 400;">Circle,</span></p> 
                                                              
                                                              <p>
                                                                <span style="font-weight: 400;">Crypts features</span></td> 
                                                                
                                                                <td>
                                                                  <span style="font-weight: 400;">3.58%</span>
                                                                </td>
                                                                
                                                                <td>
                                                                </td>
                                                                
                                                                <td>
                                                                  <span style="font-weight: 400;">1.39%</span>
                                                                </td></tr> 
                                                                
                                                                <tr>
                                                                  <td colspan="6">
                                                                    <h2>
                                                                      <span style="font-weight: 400;">Iris segmentation only</span>
                                                                    </h2>
                                                                  </td>
                                                                </tr>
                                                                
                                                                <tr>
                                                                  <td>
                                                                    <span style="font-weight: 400;">IrisSeg [</span><a href="https://github.com/cdac-cvml/IrisSeg"><span style="font-weight: 400;">project</span></a><span style="font-weight: 400;">]</span>
                                                                  </td>
                                                                  
                                                                  <td>
                                                                    <span style="font-weight: 400;">2017,</span></p> 
                                                                    
                                                                    <p>
                                                                      <span style="font-weight: 400;">Matlab</span></td> 
                                                                      
                                                                      <td>
                                                                      </td>
                                                                      
                                                                      <td>
                                                                        <span style="font-weight: 400;">ICB 2016</span>
                                                                      </td>
                                                                      
                                                                      <td colspan="2">
                                                                        <span style="font-weight: 400;">IrisSeg: A Fast and Robust Iris Segmentation Framework for Non-Ideal Iris Images</span>
                                                                      </td></tr> 
                                                                      
                                                                      <tr>
                                                                        <td>
                                                                          <span style="font-weight: 400;">IAADseg</span></p> 
                                                                          
                                                                          <p>
                                                                            <span style="font-weight: 400;">[</span><a href="http://www4.comp.polyu.edu.hk/~csajaykr/tvmiris.htm"><span style="font-weight: 400;">project</span></a><span style="font-weight: 400;">]</span></td> 
                                                                            
                                                                            <td>
                                                                              <span style="font-weight: 400;">2015,</span></p> 
                                                                              
                                                                              <p>
                                                                                <span style="font-weight: 400;">Matlab</span></td> 
                                                                                
                                                                                <td>
                                                                                  <span style="font-weight: 400;">Total-variation</span>
                                                                                </td>
                                                                                
                                                                                <td>
                                                                                  <span style="font-weight: 400;">ICCV 2015</span>
                                                                                </td>
                                                                                
                                                                                <td colspan="2">
                                                                                  <span style="font-weight: 400;">An Accurate Iris Segmentation Framework under Relaxed Imaging Constraints using Total Variation Model</span>
                                                                                </td></tr> 
                                                                                
                                                                                <tr>
                                                                                  <td>
                                                                                    <span style="font-weight: 400;">IrisSeg</span></p> 
                                                                                    
                                                                                    <p>
                                                                                      <span style="font-weight: 400;">[</span><a href="https://github.com/sbanerj1/IrisSeg"><span style="font-weight: 400;">project</span></a><span style="font-weight: 400;">]</span></td> 
                                                                                      
                                                                                      <td>
                                                                                        <span style="font-weight: 400;">2015,</span></p> 
                                                                                        
                                                                                        <p>
                                                                                          <span style="font-weight: 400;">Python</span></td> 
                                                                                          
                                                                                          <td>
                                                                                            <span style="font-weight: 400;">Geodesic Active Contours and GrabCut</span>
                                                                                          </td>
                                                                                          
                                                                                          <td>
                                                                                            <span style="font-weight: 400;">PSIVT 2015</span>
                                                                                          </td>
                                                                                          
                                                                                          <td colspan="2">
                                                                                            <span style="font-weight: 400;">Iris Segmentation using Geodesic Active Contours and GrabCut</span>
                                                                                          </td></tr> </tbody> </table> 
                                                                                          
                                                                                          <p>
                                                                                            <span style="font-weight: 400;">Iris datasets to consider:</span>
                                                                                          </p>
                                                                                          
                                                                                          <table>
                                                                                            <tr>
                                                                                              <td>
                                                                                                <b>Dataset</b>
                                                                                              </td>
                                                                                              
                                                                                              <td>
                                                                                                <b> Subset</b>
                                                                                              </td>
                                                                                              
                                                                                              <td>
                                                                                                <b>Number of</b></p> 
                                                                                                
                                                                                                <p>
                                                                                                  <b>subjects</b></td> 
                                                                                                  
                                                                                                  <td>
                                                                                                    <b>Number of</b></p> 
                                                                                                    
                                                                                                    <p>
                                                                                                      <b>images</b></td> 
                                                                                                      
                                                                                                      <td>
                                                                                                        <b>Spectrum</b>
                                                                                                      </td>
                                                                                                      
                                                                                                      <td>
                                                                                                        <b>Note</b>
                                                                                                      </td></tr> 
                                                                                                      
                                                                                                      <tr>
                                                                                                        <td rowspan="6">
                                                                                                          <span style="font-weight: 400;">CASIA</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">CASIA-Iris-Thousand</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">10,000</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">20,000</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">NIR</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                      </tr>
                                                                                                      
                                                                                                      <tr>
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">CASIA-Iris-Interval</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">Time lapse</span>
                                                                                                        </td>
                                                                                                      </tr>
                                                                                                      
                                                                                                      <tr>
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">CASIA-Iris-Lamp</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                      </tr>
                                                                                                      
                                                                                                      <tr>
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">CASIA-Iris-Twins</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">100</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">Twin</span>
                                                                                                        </td>
                                                                                                      </tr>
                                                                                                      
                                                                                                      <tr>
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">CASIA-Iris-Distance</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">At a distance</span>
                                                                                                        </td>
                                                                                                      </tr>
                                                                                                      
                                                                                                      <tr>
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">CASIA-Iris-Syn</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">1000</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">10,000</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">Synthesis</span>
                                                                                                        </td>
                                                                                                      </tr>
                                                                                                      
                                                                                                      <tr>
                                                                                                        <td rowspan="6">
                                                                                                          <span style="font-weight: 400;">ND</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">ND-IRIS-0405</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">356</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">64,980</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">NIR</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                      </tr>
                                                                                                      
                                                                                                      <tr>
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">ND-GFI</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">Gender</span>
                                                                                                        </td>
                                                                                                      </tr>
                                                                                                      
                                                                                                      <tr>
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">NDCLD15</span>
                                                                                                        </td>
                                                                                                        
                                                                                                        <td>
                                                                                                          <span style="font-weight: 400;">750 males</span></p> 
                                                                                                          
                                                                                                          <p>
                                                                                                            <span style="font-weight: 400;">750 females</span></td> 
                                                                                                            
                                                                                                            <td>
                                                                                                              <span style="font-weight: 400;">3000</span>
                                                                                                            </td>
                                                                                                            
                                                                                                            <td>
                                                                                                              <span style="font-weight: 400;">NIR</span>
                                                                                                            </td>
                                                                                                            
                                                                                                            <td>
                                                                                                              <span style="font-weight: 400;">Contact Lens</span>
                                                                                                            </td></tr> 
                                                                                                            
                                                                                                            <tr>
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">ND-CrossSensor-Iris-2013</span>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">676</span>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">29,986 from LG4000 and 116,564 from LG2200</span>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">NIR</span>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">Cross Sensor</span>
                                                                                                              </td>
                                                                                                            </tr>
                                                                                                            
                                                                                                            <tr>
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">ND-TimeLapseIris-2012</span>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">23</span>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">6797</span>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">Time lapse 2004 to 2008</span>
                                                                                                              </td>
                                                                                                            </tr>
                                                                                                            
                                                                                                            <tr>
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">ND-Iris-Template-Aging-2008-2010</span>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">11,776</span>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">Time lapse 2008 to 2010</span>
                                                                                                              </td>
                                                                                                            </tr>
                                                                                                            
                                                                                                            <tr>
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">MBGC</span>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">NIR & NIR videos</span>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">One the move</span>
                                                                                                              </td>
                                                                                                            </tr>
                                                                                                            
                                                                                                            <tr>
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">UBIRIS</span>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">261</span>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">11,102</span>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">Visible</span>
                                                                                                              </td>
                                                                                                              
                                                                                                              <td>
                                                                                                                <span style="font-weight: 400;">On the move</span></p> 
                                                                                                                
                                                                                                                <p>
                                                                                                                  <span style="font-weight: 400;">At a distance</span></td> </tr> </tbody> </table> 
                                                                                                                  
                                                                                                                  <p>
                                                                                                                    &nbsp;
                                                                                                                  </p>
                                                                                                                  
                                                                                                                  <p>
                                                                                                                    <span style="font-weight: 400;">My sources:</span>
                                                                                                                  </p>
                                                                                                                  
                                                                                                                  <ol>
                                                                                                                    <li style="font-weight: 400;">
                                                                                                                      <a href="https://kiennguyenstuff.wordpress.com/2016/07/14/iris-recognition-open-source-codes/"><span style="font-weight: 400;">Iris Recognition open-source codes</span></a>
                                                                                                                    </li>
                                                                                                                    <li style="font-weight: 400;">
                                                                                                                      <a href="https://www.quora.com/What-are-some-of-the-best-open-source-iris-recognition-libraries-available"><span style="font-weight: 400;">What are some of the best open source iris recognition libraries available?</span></a>
                                                                                                                    </li>
                                                                                                                  </ol>
                                                                                                                  
                                                                                                                  <ul>
                                                                                                                    <li>
                                                                                                                      <em>Eye Photo by Tom Tolkien <a href="http://thomastolkien.wordpress.com/">http://thomastolkien.wordpress.com/</a></em>
                                                                                                                    </li>
                                                                                                                  </ul>

 [1]: https://kiennguyenstuff.wordpress.com/2016/07/14/iris-recognition-open-source-codes/
 [2]: https://kiennguyenstuff.wordpress.com/author/thanhkien84/