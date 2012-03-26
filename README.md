Overview
==========

Basic portfolio optimization code, adapted from one of my CQF lectures

In the example, there are 4 assets:

Asset #    Return     Volatility
1          5%         7%
2          7%         12%
3          15%        30%
4          27%        60%

The correlation matrix is:
1.0  0.8  0.5  0.4
0.8  1.0  0.7  0.5
0.5  0.7  1.0  0.8
0.4  0.5  0.8  1.0

For a target return of 12%, the min variance portfolio would have this allocation:
Asset 1:   28%
Asset 2:   32%
Asset 3:   21%
Asset 4:   19%
And a portfolio std deviation of : 20.7%

(Depending on the parameters the calculations will return negative values to indicate short positions and a may return values > 100% to indicate leverage is required)

To run this code, you need 
Python: http://www.python.org/ftp/python/2.7/python-2.7.msi
And numpy: http://sourceforge.net/projects/numpy/files/NumPy/1.5.1/numpy-1.5.1-win32-superpack-python2.7.exe/download

Basic Usage
============

    return_vector = numpy.matrix((0.05, 0.07, 0.15, 0.27)).T
    stddev_vector = numpy.matrix((0.07, 0.12, 0.30, 0.60)).T
    correlation_matrix = numpy.matrix(((1.0, 0.8, 0.5, 0.4),
                                       (0.8, 1.0, 0.7, 0.5),
                                       (0.5, 0.7, 1.0, 0.8),
                                       (0.4, 0.5, 0.8, 1.0)))

    target_return = .125
    allocations, stddev = calc_min_variance_portfolio(return_vector, stddev_vector, 
                                correlation_matrix, target_return)
    print "scenario 1 - optimize portfolio for target return"
    print "target return: %.2f%%" % (target_return * 100.0)
    print "min variance portfolio:"
    print allocations
    print "portfolio std deviation: %.2f%%" % (stddev * 100.0)

    print "-" * 40
    
    target_variance = .15
    allocations, stddev, rtn = calc_max_return_portfolio(return_vector, stddev_vector, 
                                                         correlation_matrix, target_variance)
    print "scenario 2 - optimize portfolio for target variance"
    print "target variance: %.2f%%" % (target_variance * 100.0)
    print "max return:"
    print allocations
    print "portfolio std deviation: %.2f%%" % (stddev * 100.0)
    print "portfolio return: %.2f%%" % (rtn * 100.0)
																																		          print "portfolio return: %.2f%%" % (rtn * 100.0)

License
============
Public domain
