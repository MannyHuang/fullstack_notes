
======================================================================================
Mathematics
======================================================================================
1.dot product
	1.(A) and (B) dot vector => A*B*Cos(angle in between)
	2.two parrallel: 1
	3.two vertical: 0
	4.scalar
2.cross product
	1.(A) and (B) cross vector => A*B*Sin(angle in between)
	2.two parrallel: 0
	3.two vertical: at least is not 0, direction: right hand rule (from a to b, use your hand, man--)
	4.Vector
3.Position Vector:
	1.Notation: R1
	2.the vector from origin to P1
4.Distance Vector:
	1.Notation: R12 (from P1 to P2)
	2.R12= R2 - R1
	3.The distance is the magnitude of R12
5.Coordinate Systems:
	1.Non-orthogonal
		1.pray
	2.Orthogonal
		1.Catesian (x,y,z):
			1.Diffrential Length:dx,dy,dz
			2.Diffrential Area:dz=dxdy,dx=dydz, dy=dxdz
			3.Diffrential Volume:dxdydz
		2.Cylindrical (r,phi,z):
			1.Diffrential Length:dlr=dr,dlphi=r*dphi,dlz=dz
			2.Diffrential Area:drdphidz,drdz,dzdphi
			3.Diffrential Volume:rdrdphidz
		3.Sphererical (R,theta, phi):
			1.Diffrential Length:dlR=dR,dlphi=R*sin(theta)*dphi,dlz=Rdtheta
			2.Diffrential Area:dSR=R^2*sin(theta)*dphidtheta,dSphi=R*dtheta*dR,dSz=R*sin(theta)*dphi*dR
			3.Diffrential Volume:R^2*sin(theta)*dphidtheta*dphi
6.Gradient of a scalar field:
	1.differentiate in each direction
	2.scalar field => vector field
7.Directional Derivitive:
	1.(gradient) and (unit vector in the direction specified) dot product
8.Divergence:
	1. the sum of differentiation in each direction
	2. vector field =>gradient field
	3.physical meaning:
			1.positive divergence: source (net outward field)
			2.negative divergence: sink (net inward field)
			3.zero divergence: int and out (uniform e-field)
	3.divergence theorem: (volume integral)of the divergence of an e-field = (surface integral) the e-field
9.Curl:
	1.contour integral of a field
	2.stoke's theorem: (surface integral)of the curl of an b-field = (contour integral) of the b-field
10.Laplacian Operator:
	1.sum of double differentiation of a field
